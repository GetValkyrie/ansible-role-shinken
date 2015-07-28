Ansible Role: Shinken
=====================

[![Build Status](https://travis-ci.org/GetValkyrie/ansible-role-shinken.svg?branch=master)](https://travis-ci.org/GetValkyrie/ansible-role-shinken)

Installs and configures Shinken monitoring server.

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

Most useful variables are `shinken_version`, `shinken_enabled_services` and `shinken_disabled_services`.

As an example, say we have a shinken "Central" machine that do not poll nor schedule anything, and we want Shinken 2.2:

```yaml
shinken_version: '2.2'
shinken_enabled_services:
    - shinken-arbiter
    - shinken-broker
    - shinken-reactionner
    - shinken-receiver
shinken_disabled_services:
    - shinken-poller
    - shinken-scheduler
```

Then, on the "Poller" machines, swap enabled/disabled lists and here you go!

You may want to set a different path for nagios plugins:

```yaml
shinken_nagios_plugins_path: '/my/custom/path'
```

Lastly, if you need to support another distribution, add a `vars/{{ ansible_os_family }}.yml` file and set it up like the others.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: getvalkyrie.shinken }

License
-------

BSD

Author Information
------------------

This role was created in 2015 by [Christopher Gervais](http://ergonlogic.com/).
