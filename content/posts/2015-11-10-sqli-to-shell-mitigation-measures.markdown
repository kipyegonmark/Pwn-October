---
title: "SQLi to Shell - Mitigation Measures"
date: 2015-11-10 12:52:03 +0300
draft: false
category: Pentester Lab
summary: As a follow up to [this](#) Pentester Lab exercise, there exist possible countermeasures against such an attack.
---
As a follow up to [this](#) Pentester Lab exercise, there exist possible countermeasures against such an attack.

The original Pentester Lab exercise can be attempted [here](https://pentesterlab.com/exercises/from_sqli_to_shell).

### Disable Banners

During the fingerprinting stage, a banner grab was used to capture information about the web server and operating system in use.

In a Debian based environment, Apache web server can be configured to hide this information.

The required configuration file exists in this location.

``/etc/apache/apache2.conf``

Alternatively, in a derivative of Red Hat Linux the configuration file exists in this location.

``/etc/httpd/conf/httpd.conf``

Using a text editor, the user can make amendments as shown.

```
ServerSignature Off

ServerTokens Prod
```

Restarting the Apache web server will enforce this change and counter the information leakage.

### SQL Injection

SQLi could be countered through the use of sanitised user input. With the correct rules in place, SQL will reject invalid input and crucially will not run code.

Parametrised queries are used to enforce sanitised user input. 

As an example, from the penetration test the query below was used prove SQL injection.

``SELECT * FROM users WHERE name = '' OR '1'='1';``

This threat can be countered using a parameter for user input as shown.

``SELECT * FROM users WHERE name = '@name';``

With this change, user input will now only be treated as a field parameter and not as a SQL query.

### Exploitation

During the exploitation phase, the attacker gained access to hashed passwords. Furthermore password cracking was made trivial due to the use of MD5 cryptographic hash function.

[Salting](https://en.wikipedia.org/wiki/Salt_(cryptography) the password hashes would reduce the chances of the attacker retrieving a plain text version of the stored passwords.

In addition it would be beneficial to use a more suitable hash function such as SHA-256.

### Countermeasures

* Harden the web server
* Separation of user privileges - limit use of root/ admin accounts
* Disable directory listing
* Disable unused applications/ modules

### Conclusion

The [penetration test](#) exploited weaknesses in the configuration of a web application.

Using this exercise, we can prove that several steps can be implemented to make this task more difficult for the attacker i.e. threat mitigation.
