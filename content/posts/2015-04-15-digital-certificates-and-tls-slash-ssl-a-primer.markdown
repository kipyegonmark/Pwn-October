---
title: "Digital Certificates and TLS/ SSL a Primer"
date: 2015-04-15 06:59:23 +0300
draft: false
category: TLS/ SSL
summary: Digital certificates or TLS/ SSL certificates are an implementation of public key infrastructure (PKI). In simple terms digital certificates allow a trusted third party, the certificate authority, to verify the identity of the certificate owner.
---
Digital certificates or TLS/ SSL certificates are an implementation of public key infrastructure (PKI). In simple terms digital certificates allow a trusted third party, the certificate authority, to verify the identity of the certificate owner.

The use of digital certificates also enables the use of HTTP over TLS (HTTPS) to mitigate against interception and tampering of data in transit. Traditional applications include payment transactions, banking applications and email.

### Threat Actors

The original design of the Internet and its related protocols did not factor in security. An indirect result is that intercepted traffic over HTTP is viewable to [world plus dog](https://www.urbandictionary.com/define.php?term=world%20%2B%20dog).

This flaw received public attention when [Firesheep](https://codebutler.github.io/firesheep/) extension for Firefox was used to capture login credentials for social media sites over open networks.

Other threats can involve service providers [injecting ads](http://arstechnica.com/tech-policy/2013/04/how-a-banner-ad-for-hs-ok/) into web pages and more worryingly state agents [intercepting](https://www.schneier.com/blog/archives/2013/10/how_the_nsa_att.html) [and weaponising](http://www.nytimes.com/2015/04/11/technology/china-is-said-to-use-powerful-new-weapon-to-censor-internet.html?_r=0) the Internet.

The threats listed could all be mitigated by encrypting data during transmission (HTTPS) and enforcing non-repudiation by implementing digital certificates.

### Obtaining a Digital Certificate

Digital certificates are fairly easy to obtain from a certificate authority (CA). CAs might require additional information to verify ownership/ control of the domain.

As per PKI a public-private key pair is generated with the private key to be installed on the web server and the public key to be shared with clients who access the site or application.

An additional intermediate file may also be generated and this verifies the identity of the CA with a higher level CA. CAs operate on the basis of reputation and modern web browsers (I recommend either Mozilla Firefox or Google Chrome) will flag fraudulent CAs causing issues with operability.

### Self-Signed Digital Certificates

For testing purposes, a user may elect to generate self-signed digital certificates. This should only be used for internal purposes since a CA, the trusted third party, cannot verify the validity of the public key.

### Let’s Encrypt

[Let’s Encrypt](https://letsencrypt.org/), a collaborative project under the Linux Foundation launches in mid 2015 serving as an automated and [no cost](http://www.urbandictionary.com/define.php?term=Free%20as%20in%20Beer) CA.

### Conclusion

Digital certificates and encryption through HTTPS should be considered a base standard for a more secure Internet. To maintain a level of confidentiality and data integrity, communication over HTTPS should be the default option.

In a future post I will document how I obtained a digital certificate for this blog and the minor challenges experienced. Completing this exercise requires some free time and minimal technical skill.

#### Update

Let's Encrypt is currently in beta and has begun issuing certificates. As of December 3rd 2015 this [initiative](https://letsencrypt.org/2015/11/12/public-beta-timing.html) will be open to the public.

#### Update 2

As of December 18th 2015 Let's Encrypt is live on this [site](#).
