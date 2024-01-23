Introduction
============

This repository contains automation task with ansible for security team.

Configuration
=============

-

Documentation playbook
======================

* [docker](./docs/playbook/docker.md)
* [fail2ban](./docs/playbook/fail2ban.md)


using ssh-agent
===============

For using `ssh-agnet` you just use like below:
 
```bash
### Add private-key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add <path-of-ssh-private-key>

#########################################

### Remove ssh-agent process
ssh-add -D <path-of-ssh-private-key>
```
