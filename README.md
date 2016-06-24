nsq
===

A role which installs and manages NSQ.

Role ready status
-----------------

[![Build Status](http://img.shields.io/travis/retr0h/ansible-nsq.svg?style=flat-square)](https://travis-ci.org/retr0h/ansible-nsq)
[![Galaxy](http://img.shields.io/badge/galaxy-ansible--nsq-blue.svg?style=flat-square)](https://galaxy.ansible.com/list#/roles/2265)

Requirements
------------

None

Role Variables
--------------

See defaults/main.yml

Dependencies
------------

None

Example Playbook
----------------

This playbook will install nsqadmin, nsqd, nsqlookupd to each machine.

if `use_ip` set to `true`, then the configuration will use ip address to locate the services, if `false` use the hostname.

    - hosts: all
      roles:
        - role: nsq
          nsq_nsqadmin_server: true
          nsq_nsqd_server: true
          nsq_nsqlookupd_server: true
          use_ip: false

License
-------

MIT
