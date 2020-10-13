---
title: "LAMP Stack Deployment on CentOS"
date: 2016-01-18 03:28:49 +0300
draft: false
category: Home Lab
summary: The LAMP stack; for Linux, Apache, MySQL and PHP, allows a user to run dynamic websites and web applications.
---
The LAMP stack; for Linux, Apache, MySQL and PHP, allows a user to run dynamic websites
and web applications.

For this exercise, the installation and basic configuration of the LAMP stack will be
done on the existing [web server](#).

This blog uses [Octopress](#)
so the LAMP stack is purely as proof of concept.

### Installation

From shell, install and start the Apache web server as shown:

```
$ yum install httpd

$ service httpd start
```

Accessing the web server's ip address from a web browser should now return a web page.

From shell, install and start MySQL using the following:

```
$ yum install mysql-server

$ service mysqld start
```

The next step is to install PHP using:

``$ yum install php php-mysql``

### Hardening

After successful installation, basic configuration can be done to harden the web server.
Steps to take include:

* Apache should not run as root

Create a non-privileged account to run Apache. From shell:

```
$ groupadd apache

$ useradd apache -g apache -d /dev/null -s /sbin/nologin
```

Using a text editor, modify the Apache configuration __httpd.conf__

```
$ User apache

$ Group apache
```

* Restrict access permissions

This step intends to restrict access to the Apache directory by modifying permissions.
From the shell:

```
$ chown -R root:root /etc/httpd

$ chmod -R 640 /etc/httpd
```

Additionally, restrict access permissions for Apache configuration and logs.

```
$ chmod -R 640 /etc/httpd/conf

$ chmod -R 640 /var/log/httpd
```

* Minimise information leakage

It is important to minimise [information leakage](#).
To meet this objective modify the Apache configuration __httpd.conf__

```
ServerSignature Off

ServerTokens ProductOnly

ServerName www.mywebsite.com:80
```

* Basic MySQL configuration

By default, MySQL has a root account with a blank password. This and other basic
configuration changes can be made from terminal by running the following:

``$ /usr/bin/mysql_secure_installation``
