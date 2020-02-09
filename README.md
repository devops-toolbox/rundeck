Role Name
=========

rundeck: Rundeck

[![Build Status](https://travis-ci.org/cmihai-ansible/rundeck.svg?branch=master)](https://travis-ci.org/cmihai-ansible/rundeck)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.rundeck](https://galaxy.ansible.com/devopstoolbox.rundeck)

```bash
ansible-galaxy install devopstoolbox.rundeck
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
rundeck_packages_state: present
rundeck_remove_packages: true
rundeck_enable_service: true
rundeck_enable_selinux: true
rundeck_copy_templates: true
rundeck_firewall_configure: true
rundeck_firewall_rules:
  - service: ssh
  - port: 3389
rundeck_users:
  - user: devops
    group: docker
rundeck_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install rundeck on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: rundeck is configured
      import_role:
        name: devopstoolbox.rundeck
      vars:
        rundeck_packages_state: present
        rundeck_remove_packages: true
        rundeck_enable_service: true
        rundeck_enable_selinux: true
        rundeck_copy_templates: true
        rundeck_firewall_configure: true
        rundeck_firewall_rules:
          - service: ssh
          - port: 3389
        rundeck_users:
          - user: devops
            group: docker
        rundeck_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: rundeck
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
