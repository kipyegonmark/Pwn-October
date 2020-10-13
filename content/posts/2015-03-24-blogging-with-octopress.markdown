---
title: "Blogging With Octopress"
date: 2015-03-24 07:46:17 +0300
draft: false
Category: Octopress
summary: Octopress described as a blogging framework for hackers, is an implementation of Jekyll
---
[Octopress](http://octopress.org/); described as a blogging framework for hackers, is an implementation of Jekyll, the same implementation used by [GitHub Pages](https://pages.github.com/).

Composing of posts is done in Markdown and with the benefit of Git, backup and version control can be implemented.

For this exercise, it is advisable that one is comfortable using a terminal/ command line
 
### Getting Started
 
I chose Octopress because it is simple to use and deploy. Content is composed in Markdown markup language and plugins add extra functionality to create a clean and presentable site.
  
Octopress has quality [documentation](http://octopress.org/docs/) and requires minimal programming knowledge to use.

As a learning experience, this is an excellent way to pick up some experience of both the terminal and [Git](http://www.git-scm.com) version control system.
 
### The Challenges
 
Jekyll in GitHub pages runs in safe mode and this disables symlinked files. With this feature disabled, GitHub will return symlink error messages during attempted deployment.

This is a documented [security issue](https://github.com/jekyll/jekyll/pull/315) from using symlinks with Jekyll.
 
At this point I elected to use a webhosting service for deployment. Octopress can deploy with rsync via SSH which is fast and can be secure thanks to public-key cryptography.
 
* It is a good idea to verify with your web host if they do offer SSH access.
* [Generate](http://www.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man1/ssh-keygen.1?query=ssh-keygen&sec=1) strong authentication keys for SSH. The minimum recommended key length is currently 2048 bits.
* Keep your private keys safe!

Additionally I will advise against using FTP because it does not encrypt traffic and is vulnerable to interception.
 
I will attempt to use secure copy (scp) and FileZilla using secure FTP as alternative deployment methods. These options shall be discussed in a future post.
