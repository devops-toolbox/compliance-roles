Role Name
=========

compliance-roles: Compliance-roles

[![Build Status](https://travis-ci.org/cmihai-ansible/compliance-roles.svg?branch=master)](https://travis-ci.org/cmihai-ansible/compliance-roles)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.compliance-roles](https://galaxy.ansible.com/devopstoolbox.compliance-roles)

```bash
ansible-galaxy install devopstoolbox.compliance-roles
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
compliance-roles_packages_state: present
compliance-roles_remove_packages: true
compliance-roles_enable_service: true
compliance-roles_enable_selinux: true
compliance-roles_copy_templates: true
compliance-roles_firewall_configure: true
compliance-roles_firewall_rules:
  - service: ssh
  - port: 3389
compliance-roles_users:
  - user: devops
    group: docker
compliance-roles_selinux_booleans:
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
- name: Install compliance-roles on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: compliance-roles is configured
      import_role:
        name: devopstoolbox.compliance-roles
      vars:
        compliance-roles_packages_state: present
        compliance-roles_remove_packages: true
        compliance-roles_enable_service: true
        compliance-roles_enable_selinux: true
        compliance-roles_copy_templates: true
        compliance-roles_firewall_configure: true
        compliance-roles_firewall_rules:
          - service: ssh
          - port: 3389
        compliance-roles_users:
          - user: devops
            group: docker
        compliance-roles_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: compliance-roles
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
