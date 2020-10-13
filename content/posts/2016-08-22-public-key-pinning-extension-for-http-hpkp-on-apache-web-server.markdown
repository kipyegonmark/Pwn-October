---
title: "Public Key Pinning Extension for HTTP (HPKP) on Apache Web Server"
date: 2016-08-22 09:00:25 +0300
draft: false
category: Primers
summary: _HPKP_ as defined in RFC7469, ['tells a web client to associate a specific cryptographic public key with a certain web server'](https://developer.mozilla.org/en/docs/Web/Security/Public_Key_Pinning).
---
__HPKP support has been dropped by all major browsers. The feature was complex to implement and had the potential to break website access.__

_HPKP_ as defined in RFC7469, ['tells a web client to associate a specific cryptographic public key with a certain web server'](https://developer.mozilla.org/en/docs/Web/Security/Public_Key_Pinning).

Used in combination with [HTTP Strict Transport Security](#), HPKP can be a strong defense against man in the middle (MITM) attacks by enforcing certificate chain validation.

In this event, the threat agent is a rogue or a compromised certificate authority such as Diginotar's [fraudulent issuance of google.com certificates](https://blog.mozilla.org/security/2011/08/29/fraudulent-google-com-certificate/).

### Weaknesses

HPKP relies in _trust on first use_. On initial connection, the web client cannot validate the certificate chain . This means [Eve](https://en.wikipedia.org/wiki/Alice_and_Bob) can potentially intercept the initial connection and perform an MITM.

Major websites (such as [Google](https://cs.chromium.org/chromium/src/net/http/transport_security_state_static.json?l=49) and [Facebook](https://cs.chromium.org/chromium/src/net/http/transport_security_state_static.json?l=170)) have pre-shared keys hardcoded into Chrome and Firefox as a mitigation. However this is not a practical solution for the rest of the Internet. In practice, future connection requests to the valid web host should then return an error to the client.

As of August 2016, [browser support](http://caniuse.com/#search=HPKP) for HPKP is limited to Firefox, Chromium and Opera.

### Deployment

#### Caution

If incorrectly configured, HPKP can cause a website to become inaccessible. For testing the __Public-Key-Pins-Report-Only__ directive can be used or alternatively the website owner can set a low value for __max-age__.

### Policy Configuration

The standards document requires at least two pins to enforce HPKP. It is at the website owner's discretion on which pins are appropriate for deployment.

For this exercise I elected to rely on Github's [HPKP policy](https://report-uri.io/home/pkp_analyse/https%3A%2F%2Fgithub.com). The reasoning here is that [Github](http://github.com/) is one of the largest websites that supports HPKP and their setup seems robust enough for production use.

The directives as used in the above policy are described here:

__pin-sha="..."__

This is a base64 string that corresponds to the pin for a public key. I intend to pin two root keys, one intermediate key and two offline backup keys. 

#### Key Generation

For the root keys, I selected (Identrust) DST Root CA X3 root certificate and the newer ISRG Root X1 by Let's Encrypt and for the intermediate certificate I chose Let's Encrypt Authority X3.

DST Root CA X3 root certificate is sourced from [here](https://www.identrust.com/certificates/trustid/install-nes36.html) and the Let's Encrypt certificate keys are available [here](https://letsencrypt.org/certificates/).

Using the retrieved information, the next step is to generate the base64 encoded hashes as shown below:

```
$ openssl x509 -in certificate.pem -pubkey -noout | openssl pkey -pubin 
-outform der | openssl dgst -sha256 -binary | openssl enc -base64

$ curl https://letsencrypt.org/certs/isrgrootx1.pem | openssl x509 -pubkey | openssl pkey 
-pubin -outform der | openssl dgst -sha256 -binary | base64

$ curl https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.pem | openssl x509 
-pubkey | openssl pkey -pubin -outform der | openssl dgst -sha256 -binary | 
base64
```

The two offline keys are generated and stored offline as backup keys in the event the Let's Encrypt CA becomes unavailable.

Generation of the private key and the required base64 hash is shown below.

Replace foo.com with a name of your choice.

```
$ openssl req -nodes -sha256 -newkey rsa:4096 -keyout 'foo.com.rsa.key' -out 'foo.com.rsa.csr'

$ openssl req -pubkey < foo.com.csr | openssl pkey -pubin -outform der | openssl dgst 
-sha256 -binary | base64
```

__max-age=5184000__

This value in seconds is equivalent to two months. A shorter duration offers less protection to users while a higher duration presents a risk where pin validation might fail.

* For testing remember to use a smaller value such as 60. A mistake could potentially break access to a domain.
        
__includeSubDomains__

This optional directive is self-descriptive and is used to apply the HPKP policy to all subdomains.

__report-uri__

This is an optional directive through which pin validation failures are to be reported. The value should obviously be to a different domain. 

A real time reporting tool is included with report-uri.io for reporting pin validation errors.

Using the directives described above, the result is should be similar to the snippet below. 

```
Header set Public-Key-Pins 
"pin-sha256=\"Vjs8r4z+80wjNcr1YKepWQboSIRi63WsWXhIMN+eWys="; 
pin-sha256=\"YLh1dUR9y6Kja30RrAn7JKnbQG/uEtLMkBgFF2Fuihg=\"; 
pin-sha256=\"47DEQpj8HBSa+/TImW+5JCeuQeRkm5NMpJWZG3hSuFU=\"; 
pin-sha256=\"BnCc92LNTmq+v0mGoN13pbuR/d8WcOBYtZCCMBKwrmo=\"; 
pin-sha256=\"MBCWEpJFZIJKp3Tjy4WTIL2AcL91yV4Zo2PfsHyiaVQ=\"; 
report-uri=\"https://55343e1861289e8df8aa157da3c58796.report-uri.io/r/default/hpkp/enforce\"; 
max-age=5184000; 
includeSubdomains;"
```

In Apache, the snippet is to be added to virtual hosts located by default in __/etc/httpd/conf.d/ssl.conf__. Restarting the web server should now enforce public key pinning.

### Testing

Using Firefox, one can verify that HPKP is enabled using the network tool bundled with 'Web developer' Tools. 

Alternatively online tools by report-uri.io found [here](https://report-uri.io/home/pkp_analyse) or a complete report using Qualys [SSL Server Test](https://www.ssllabs.com/ssltest/analyze.html) can be used to test a domain.

### Conclusion

At the date of posting, this website has successfully deployed HTTP Public Key Pinning. 

### References

* [RFC7469](https://tools.ietf.org/html/rfc7469)
* [report-uri.io](report-uri.io) - A great utility that offers tools to configure and deploy a HPKP policy
* Mozilla Developer Network article on [Public Key Pinning](https://developer.mozilla.org/en/docs/Web/Security/Public_Key_Pinning)
* Github's [HPKP policy](https://report-uri.io/home/pkp_analyse/https%3A%2F%2Fgithub.com)
* [HTTP Public Key Pinning Extension HPKP for Apache, NGINX and Lighttpd](https://raymii.org/s/articles/HTTP_Public_Key_Pinning_Extension_HPKP.html#Apache)
* Scott Helme's post on [HPKP](https://scotthelme.co.uk/hpkp-http-public-key-pinning/)
* [Activating HTTP Public Key Pinning (HPKP) on Let's Encrypt](https://ithenrik.com/blog/posts/activating-http-public-key-pinning-hpkp-on-lets-encrypt)
