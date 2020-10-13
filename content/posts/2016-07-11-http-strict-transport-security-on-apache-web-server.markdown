---
title: "HTTP Strict Transport Security on Apache Web Server"
date: 2016-07-11 13:21:22 +0300
draft: false
category: Primers
summary: In this exercise, the objective is to enforce HTTP Strict Transport Security (HSTS) on an Apache web server. This is an update to the SSL/ TLS certificate deployment as documented [here](#).
---
In this exercise, the objective is to enforce HTTP Strict Transport Security (HSTS) on an Apache web server. This is an update to the SSL/ TLS certificate deployment as documented [here](#).

From Wikipedia, [HSTS](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) _'allows web servers to declare that web browsers (or other complying user agents) should only interact with it using secure HTTPS connections, and never via the insecure HTTP protocol'_.

### Requirements

* The Apache [mod_headers](https://httpd.apache.org/docs/current/mod/mod_headers.html) extension must be enabled.
* All HTTP trafic on the web server must be redirected to HTTPS.
* All subdomains must be served over HTTPS. This includes the _www_ subdomain.
* The web server must continuously be accessible through HTTPS.
Failure to meet this requirement could break access to the website for an extended period of time.

### Deployment

In the SSL/ TLS configuration file, the following segment should be amended. In Apache, this is located by default at __/etc/httpd/conf.d/ssl.conf__.

```
# HSTS (mod_headers is required) (15768000 seconds = 6 months)
Header always set Strict-Transport-Security "max-age=15768000"
```

After restarting Apache, the website should be ready for submission to the Chrome [HSTS preload list](https://hstspreload.appspot.com/). This list is supported by most [major browsers](http://caniuse.com/#feat=stricttransportsecurity).

At the time of posting, this [site](#) contains no errors and is pending submission to the list.

#### Update

As of 25th August 2016, this site is included in Chrome's HSTS preload list. In practice no modern browser should permit an insecure HTTP connection to the website.

### References

* [Mozilla SSL Configuration Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/)
* [Chrome HSTS preload list](https://hstspreload.appspot.com/)
