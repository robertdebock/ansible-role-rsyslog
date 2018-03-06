rsyslog
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-rsyslog.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-rsyslog)

Provides rsyslog for your system.

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

None known

Dependencies
------------

You may use this role to prepare your system:

- robertdebock.bootstrap

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.rsyslog
```

Install this role using `galaxy install robertdebock.rsyslog`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
