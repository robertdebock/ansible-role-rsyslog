# [rsyslog](#rsyslog)

Install and configure rsyslog on your system.

|Travis|GitHub|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-rsyslog.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-rsyslog)|[![github](https://github.com/robertdebock/ansible-role-rsyslog/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-rsyslog/actions)|[![quality](https://img.shields.io/ansible/quality/22988)](https://galaxy.ansible.com/robertdebock/rsyslog)|[![downloads](https://img.shields.io/ansible/role/d/22988)](https://galaxy.ansible.com/robertdebock/rsyslog)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-rsyslog.svg)](https://github.com/robertdebock/ansible-role-rsyslog/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.rsyslog
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for rsyslog

# To configure a server to reveice logs, set rsyslog_receiver to yes.
# Not setting this value will not configure the server tor receive logs.
# rsyslog_receiver: yes

# To forward logs to another server, set rsyslog_remote to the hostname or
# the ipaddress of the receiving rsyslog server.
# Not setting this variable will not forward logs.
# rsyslog_remote: server1.example.com

# If rsylog_remote is set, sets the "selector" pattern for determining which
# messages to send to the remote server.  Default "*.*" sends everything.
# See `man rsyslog.conf`.
rsyslog_remote_selector: "*.*"

# If rsylog_remote is set, use TCP if yes. UDP if no.
rsyslog_remote_tcp: yes

# If rsylog_remote is set, destination port to use.
rsyslog_remote_port: 514

# Set the mode for new directories; only available in legacy template.
rsyslog_dircreatemode: "0700"

# Set the mode for new files; only available in legacy template.
rsyslog_filecreatemode: "0644"

# Set the mods enabled
rsyslog_mods:
  - imuxsock
  - imjournal

# Configure rsyslog minimally (may be in conflict with custom configuration files)
rsyslog_deploy_default_config: yes

# Use the (obsolete) legacy, pre-v6 configuration file format, or the more
# modern # 'advanced' configuration file format available in v6 and up. The
# default is to use the 'legacy' format to not change config files for
# existing users of this role out of the blue.
# More information on the different formats on the rsyslog website:
# https://www.rsyslog.com/doc/v8-stable/configuration/conf_formats.html
rsyslog_config_file_format: legacy
```

## [Requirements](#requirements)

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

## [Status of requirements](#status-of-requirements)

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/rsyslog.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|alpine|all|
|amazon|all|
|el|7, 8|
|debian|buster, bullseye|
|fedora|all|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| archlinux/base | target not found: rsyslog |


## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-rsyslog) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-rsyslog/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.

- [foonix](https://github.com/foonix)
- [benformosa](https://github.com/benformosa)
- [wzzrd](https://github.com/wzzrd)

## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
