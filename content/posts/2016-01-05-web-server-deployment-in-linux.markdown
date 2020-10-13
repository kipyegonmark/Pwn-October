---
title: "Web Server Deployment in Linux"
date: 2016-01-05 13:48:37 +0300
draft: false
Category: Home Lab
summary: As an update to this blog, I have elected to migrate to a web server that I have full control over.
---
As an update to this blog, I have elected to migrate to a web server that I have full 
control over. This is beneficial for purposes of testing and deploying new tools; however 
at an increased administrative cost.

For reasons of practicality and economics, this exercise will be implemented in the cloud. 
A locally hosted virtual machine will act as a staging area before deployment.

In this exercise I intend to build a secure and robust web server. This point is important 
because this will be an Internet facing device.

For the web server, a VM running a clean installation of CentOS 7 is required.

### Objectives

* Give user minimal privileges
* Minimise attack surface
* Configure security tools

### Minimise User Account Privileges

For security it is important that users do not run as root. The intention being to reduce 
the risk of abuse either unknowingly or maliciously.

To achieve this objective we shall enforce the following:

* Set a strong password for root
* Set password quality requirements
* Limit root access

If root access is required, it is good practice to use the __setuid__ program __sudo__.

### Minimise Attack Surface

The [attack surface](https://www.sans.edu/research/security-laboratory/article/did-attack-surface) 
refers to vectors that can be exploited to gain unauthorised access to a system.

Unused (and obsolete) services such as telnet and print servers can be disabled.

### Configure Security Tools

To complete this objective, we are required to implement a firewall and [SELinux](http://selinuxproject.org/page/Main_Page).

Our CentOS 7 VM has __iptables__ setup by default. This shall be used to implement a host based firewall on our web server.

As our web server has a limited role, we can setup rules to only allow traffic on ports 80 for HTTP, 443 for HTTPS and port 22 for SSH for remote access.

Security Enhanced Linux (SELinux) is intended to give greater access control to users on a 
Linux system. SELinux takes a predefined policy and enforces _mandatory access control_.

### Conclusion

In a future post I shall go into the technical configuration used to implement the firewall and SELinux.
