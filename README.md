toni.certificates
============

Ansible role to create SSL-certificates with certbot.

TODO: Description and playbook example.

Requirements
------------

Openresty with application specific setup.

Role Variables
--------------
```bash
letsencrypt_endpoint: 'https://acme-v02.api.letsencrypt.org/directory'
#For wildcard options, have a lokk at https://github.com/unistra/bigbluebutton -> Manage SSL certificates
```

Example Task
----------------
This task has to be used after domain specific openresty setup.

```yaml
- name: set cert facts 
  include_role:
    name: certificates
    tasks_from: certbot_facts
  vars:
    certbot_server: "test.mytestserver.de"
```

License
-------

The wildcard part is bases on:
https://github.com/unistra/bigbluebutton/tree/master/roles/certificates

The part for ad-hoc letsencrypt certificates (tasks/cerbot*) is under 
MIT

Author Information
------------------

T.Nissen


