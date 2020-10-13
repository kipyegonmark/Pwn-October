---
title: "SSL/ TLS Certificate Deployment"
date: 2016-01-19 20:44:57 +0300
draft: false
category: Home Lab
summary: SSL and its successor protocol [TLS](#) enable secure connections over an inherently insecure Internet.
---
SSL and its successor protocol [TLS](#) enable secure connections over an inherently insecure Internet. Through the use of HTTPS, confidentiality, integrity and availability of a service can be more strongly enforced.

In this exercise, the objective is to correctly configure and install an TLS certificate 
on the [web server](#) built earlier.

[Let's Encrypt](https://letsencrypt.org/howitworks/) provides easier access to trusted TLS certificates. At the time of posting, the project is still in beta and installation on Enterprise Linux including CentOS has to performed manually.
 
### Getting the Certificate

From terminal, run the following commands:
 
``$ git clone https://github.com/letsencrypt/letsencrypt1``
 
``$ cd letsencrypt``
 
Replace __mydomain.com__ with the target domain:
 
``$ ./letsencrypt-auto certonly --manual -d mydomain.com -d``
 
This will create temporary files that the certificate authority will use to validate the  given request.
 
This next step requires a new shell terminal running with root privilege.
 
``$ mkdir -p /var/www/html/.well-known/acme-challenge``
 
``$ cd /var/www/html``
 
From the first terminal, copy and paste the string  of text starting from __printf "%s"__.
 
Returning to the first shell, pressing enter should return a confirmation message. If successful, the generated certificate and chain are now stored at the location __/etc/letsencrypt/live/mydomain.com/fullchain.pem__.

### Configuration

This next step is the _manual_ configuration, enabling the web server to correctly use  the installed certificate.
 
Using a text editor, the following amendments are made to __/etc/httpd/conf.d/ssl.conf__.

```
&ltVirtualHost *:443&gt
    ...
    SSLEngine on
    SSLCertificateFile      SSLCertificateFile /etc/letsencrypt/live/mydomain.com/cert.pem
    SSLCertificateKeyFile   /etc/letsencrypt/live/mydomain.com/privkey.pem
    SSLCACertificateFile    /etc/letsencrypt/live/mydomain.com/chain.pem


    # HSTS (mod_headers is required) (15768000 seconds = 6 months)
    Header always set Strict-Transport-Security "max-age=15768000"
    ...
&lt/VirtualHost&gt

# modern configuration, tweak to your needs
SSLProtocol             all -SSLv3 -TLSv1
SSLCipherSuite          ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!3DES:!MD5:!PSK
SSLHonorCipherOrder     on
    SSLCompression          off
    SSLSessionTickets       off

    # OCSP Stapling, only in httpd 2.3.3 and later
    SSLUseStapling          on
    SSLStaplingResponderTimeout 5
    SSLStaplingReturnResponderErrors off
SSLStaplingCache        shmcb:/var/run/ocsp(128000)
```

### Conclusions

* This configuration will break HTTPS on obsolete browsers therefore it is the service owner's discretion on whether to support weaker cryptographic protocols or additionally offer the service through HTTP.

* Remember to enable port 443 on the web server ;-)

### References

* Let's Encrypt [documentation](https://letsencrypt.readthedocs.org/en/latest/)
* Let's Encrypt community [page](https://community.letsencrypt.org/)
* Mozilla has an SSL configurator for various web servers and requirements. Link [here](https://mozilla.github.io/server-side-tls/ssl-config-generator/)
* Qualys have a tool to test server SSL/ TLS configurations. The tool can be found [here](https://www.ssllabs.com/index.html).
At the time of posting, this [site](#) is rated at A+
