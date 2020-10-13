---
title: "Deploying Lightweight Directory Services using OpenLDAP"
date: 2016-07-04 18:00:39 +0300
draft: false
category: Primers
Summary: In this exercise, the objective is to deploy [Lightweight Directory Access Protocol](https://tools.ietf.org/html/rfc4511) (LDAP) in the Samba environment initially deployed [here](#).
---
In this exercise, the objective is to deploy [Lightweight Directory Access Protocol](https://tools.ietf.org/html/rfc4511) (LDAP) in the Samba environment initially deployed [here](#). 

To achieve this goal the [standalone LDAP daemon](http://linux.die.net/man/8/slapd) (slapd) is to be installed and configured.

### OpenLDAP

From the source website, [OpenLDAP](http://www.openldap.org/) is "an open source implementation of the Lightweight Directory Access Protocol".

### Installation

Before [installation](http://www.openldap.org/doc/admin24/quickstart.html), OpenLDAP has the following prerequisite packages:

* nss\_ldap
* pam\_ldap
* smbldap-tools

OpenLDAP can be installed through a package manager or from source.

### Configuration

After successful installation, use a text editor to modify the configuration file. By default this is located at __/usr/local/etc/openldap/slapd.ldif__.

A sample configuration for __contoso.com__ is as shown.

```
dn: olcDatabase=mdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcMdbConfig
olcDatabase: mdb
OlcDbMaxSize: 1073741824
olcSuffix: dc=contoso,dc=com
olcRootDN: cn=Administrator,dc=contoso,dc=com
olcRootPW: secret
olcDbDirectory: /usr/local/var/openldap-data
olcDbIndex: objectClass eq</code></pre>
```

For use by slapd, the configuration file is imported by running the command shown.

``$ su root -c /usr/local/sbin/slapadd -F /usr/local/etc/cn=config -l /usr/local/etc/openldap/slapd.ldif``

If configuration is successful, slapd can be started using the following command.

``$ su root -c /usr/local/libexec/slapd -F /usr/local/etc/cn=config``

### Notes

By default, slapd grants read access to everybody. For security reasons it is important to enable access controls as documented [here](http://www.openldap.org/doc/admin24/security.html).

### References

* [Open LDAP Software Admin Guide](http://www.openldap.org/doc/admin24/)
