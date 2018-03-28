rsyslog
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rsyslog.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rsyslog)

Provides rsyslog for your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/rsyslog.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

None known

Dependencies
------------

You may use this role to prepare your system:

- [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap/)

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.6|yes|yes|yes|
|alpine-3.7|yes|yes|yes|
|centos-6|yes|yes|yes|
|centos-7|yes|yes|yes|
|debian-buster|yes|yes|yes|
|debian-jessie|yes|yes|yes|
|debian-stretch|yes|yes|yes|
|debian-wheezy|yes|yes|yes|
|fedora-26|yes|yes|yes|
|fedora-27|yes|yes|yes|
|opensuse-42.2|yes|yes|yes|
|opensuse-42.3|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|
|ubuntu-trusty|yes|yes|yes|
|ubuntu-xenial|yes|yes|yes|

Example Playbook
----------------

Here is how to setup an rsyslog server:
```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.rsyslog
      rsyslog_receiver: yes
```

Here is how to setup an rsyslog client:
```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.rsyslog
      rsyslog_remote: server1.example.com
```

You can (probably better) set these variables in group_vars.

Install this role using `galaxy install robertdebock.rsyslog`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
