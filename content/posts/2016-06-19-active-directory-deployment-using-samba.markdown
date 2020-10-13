---
title: "Active Directory Deployment using Samba"
date: 2016-06-19 20:39:10 +0300
draft: false
category: Primers
Summary: Active Directory (AD) is a Microsoft technology that provides services within a Windows domain environment.
---
Active Directory (AD) is a Microsoft technology that provides services within a Windows domain environment.

In this exercise we will use [Samba4](https://www.samba.org/), a [free software](https://www.gnu.org/philosophy/free-sw.html) implementation to deploy AD services from a CentOS 7 server.

The AD services to be deployed are:

* [Domain Services](https://technet.microsoft.com/en-us/library/cc770946(v=ws.10\).aspx)
* [Certificate Services](https://technet.microsoft.com/en-us/library/cc770357)
* [Rights Management Services](https://technet.microsoft.com/en-us/library/cc771234)
* [Lightweight Directory Services](https://technet.microsoft.com/en-us/library/cc731868)

### Prerequisites

* DNS resolution is a critical function for domain controllers and domain joined computers. To minimise the risk of authentication failures or inaccessible resources, it is good practice to use either a static IP address or deploy DHCP reservation.

* This deployment requires installation of Samba from source, linked [here](https://wiki.samba.org/index.php/Build_Samba_from_source).
Samba4 requires [Heimdal Kerberos](http://www.h5l.org/) implementation to deploy AD services. This implementation conflicts with the system supplied MIT Kerberos that ships with CentOS and RHEL.

* This setup assumes a new domain setup. 

### AD Provisioning

After successful installation, we are first required to provision a new domain. Provisioning creates an AD database and is similar in function to __dcpromo.exe__ in pre 2012 versions of Windows Server.

From terminal, we execute the following.

``$ samba-tool domain provision --use-rfc2307 --interactive``

A sample configuration is as shown.

```
Realm: CONTOSO.COM
Domain: CONTOSO
Server Role: dc
DNS backend: SAMBA_INTERNAL
Administrator password: P3ssw0rd_
```

Do note that the administrator password must meet password complexity requirements for Microsoft domain and local user accounts. The full set of requirements can be found [here](https://technet.microsoft.com/en-us/library/cc786468%28v=ws.10%29.aspx).

We can then start the Samba AD domain controller.

``$ samba4``

If initial configuration was successful, we can attempt to connect to the default __netlogon__ share using the credentials created during provisioning.

### Kerberos

The Kerberos protocol enables secure network authentication of clients and servers. A working configuration of Kerberos is created during the provisioning phase. 

To verify that Kerberos is working, the __kinit__ utility can be used to obtain a ticket.

```
$ kinit administrator@CONTOSO.COM
$ Password for administrator@CONTOSO.COM: P3ssw0rd_
```

* The realm must always be specified in uppercase!

We then run __klist__ to verify that Kerberos is working and has issued a ticket.

### Conclusion

In a future post, we will deploy LDAP and a certificate authority in the context of AD services.

* Updated to include information on Kerberos.

### References

* RHEL [Active Directory Integration Deployment Guidelines](https://access.redhat.com/sites/default/files/attachments/rhel-ad-integration-deployment-guidelines-v1.5.pdf)
