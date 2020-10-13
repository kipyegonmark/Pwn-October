---
title: "Firewall Deployment on a Linux Web Server"
date: 2016-01-13 19:06:50 +0300
draft: false
category: Home Lab
summary: For the second part of our web server [deployment](#), we are required to deploy a firewall.
---
For the second part of our web server [deployment](#), we are required to deploy a firewall.

As our web server has a single role, this should be a quick and simple deployment.

### Introduction to iptables

By default CentOS 7 comes installed with iptables/ netfilter which uses a list of user defined rules to filter traffic.

Iptables provides the user interface and netfilter; a kernel module, enforces the rules.

User defined rules are placed into __chains__ that determine the action to be enforced. 
These actions are referred to as __targets__.

The predefined chains are:

* __INPUT__ - packets destined for the host
* __OUTPUT__ - packets originating from the host
* __FORWARD__ - packets that are being routed by the host

In addition, user defined chains can be referred to using __RH-Firewall-1-INPUT__.

The default targets are:

* __ACCEPT__
* __DROP__
* __REJECT__

The targets are self-descriptive in terms of their functions. REJECT and DROP differ in 
that REJECT will send a reply to the source and DROP will not send a reply.

### Deployment

For our simple web server, the objective is to only allow SSH, HTTP and HTTPS while 
blocking all other incoming traffic.

Root access is required and it is important to enable SSH before any changes are made.

A sample to enable port 22 from shell is shown below:

``$ iptables -I INPUT -p tcp --dport 22 -j ACCEPT``

We are then required to explicitly block incoming traffic. To enforce this rule, the 
default INPUT policy has to be changed to __Explicit Allow__. From shell this can be 
enforced through the following snippet:

``$ iptables -P INPUT DROP``

Once the policy is enforced, we can now set the ports listed above to open.

Depending on user requirements, traffic to DNS and ICMP ports can also be considered.

It is then important to save the changes and restart the firewall service to enforce our 
new rules.

```
$ iptables save

$ service iptables restart
```

### Conclusion

By enforcing firewall rules on our web server, we have enhanced control over our Internet 
facing VM. Additional rules can be enforced to limit or allow access to defined ip 
addresses, ports and protocols.

### References

* [IP tables](https://wiki.centos.org/HowTos/Network/IPTables)
