---
title: "SELinux Deployment"
date: 2016-01-14 19:49:31 +0300
draft: false
category: Home Lab
summary: Security Enhanced Linux (SELinux) is an implementation of mandatory access control allowing a stricter enforcement of access policies for users and applications.
---
Security Enhanced Linux (SELinux) is an implementation of __mandatory access control__ 
allowing a stricter enforcement of access policies for users and applications.

The primary difference with how access control is managed by default in Linux, is that 
users and applications cannot override set policies.

As an implementation of a layered security approach, this can be particularly important 
in the event of unauthorised access to the system.

SELinux has three modes of operation:

* __Enforcing__ - the default setting, denies access and logs actions
* __Permissive__ - grants access with warnings and logs actions
* __Disabled__ - SELinux is off

Being a flavour of Enterprise Linux, our CentOS web server [deployment](#) 
comes with SELinux in its default mode.

The goal of this exercise is to set SELinux to its default mode thus enforcing least 
privilege access. 

From shell this can be verified as shown:

``getenforce``

### References

* [SELinux Project](http://selinuxproject.org/page/Main_Page)
* [The SELinux Notebook](http://freecomputerbooks.com/books/The_SELinux_Notebook-4th_Edition.pdf)
