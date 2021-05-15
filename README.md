toni.certificates
============

This role can be used to create a valid SSL-Certificate with the help of Let’s Encrypt ACMEv2 API, certbot and HTTP Challenge which is automaticly resolved and Certificate gets installed in Openresty. 
It is also possible to use allready received Certificates (p.e. wildcard certs). This is archived through the integration of some code from
https://github.com/unistra/bigbluebutton/blob/master/roles/certificates/tasks/main.yml

TODO: Add simple example for existing wildcard

Requirements
------------

Openresty with application specific setup.

Role Variables for creating SSL-Certificate
--------------
```bash
#Production
letsencrypt_endpoint: 'https://acme-v02.api.letsencrypt.org/directory'
#Staging / Test
#letsencrypt_endpoint: 'https://acme-staging-v02.api.letsencrypt.org/directory'
```

Example Task
----------------
This role does not run on its own. It is used with **toni.openresty** and any application role (p.e. wordpress, corteza, whatever...) 
This task has to be run after domain specific openresty setup and **it is used from within application role**.
Have a look at the tasks in **toni.corteza** role to get a clue. 


```yaml
- name: set cert facts 
  include_role:
    name: toni.certificates
    tasks_from: certbot_facts
  vars:
    certbot_server: "{{ nginx_subdomain }}{{ nginx_domain }}"
```

License
-------

The wildcard part (tasks/main.yml & tasks/facts.yml) is based on:
https://github.com/unistra/bigbluebutton/tree/master/roles/certificates

The part for ad-hoc letsencrypt certificates (tasks/cerbot*) is under 
MIT

Author Information
------------------

T.Nissen