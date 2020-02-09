Role Name
=========

openshift-install: Openshift-install

[![Build Status](https://travis-ci.org/cmihai-ansible/openshift-install.svg?branch=master)](https://travis-ci.org/cmihai-ansible/openshift-install)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.openshift-install](https://galaxy.ansible.com/devops-toolbox.openshift-install)

```bash
ansible-galaxy install devops-toolbox.openshift-install
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
openshift-install_packages_state: present
openshift-install_remove_packages: true
openshift-install_enable_service: true
openshift-install_enable_selinux: true
openshift-install_copy_templates: true
openshift-install_firewall_configure: true
openshift-install_firewall_rules:
  - service: ssh
  - port: 3389
openshift-install_users:
  - user: devops
    group: docker
openshift-install_selinux_booleans:
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
- name: Install openshift-install on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: openshift-install is configured
      import_role:
        name: devops-toolbox.openshift-install
      vars:
        openshift-install_packages_state: present
        openshift-install_remove_packages: true
        openshift-install_enable_service: true
        openshift-install_enable_selinux: true
        openshift-install_copy_templates: true
        openshift-install_firewall_configure: true
        openshift-install_firewall_rules:
          - service: ssh
          - port: 3389
        openshift-install_users:
          - user: devops
            group: docker
        openshift-install_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: openshift-install
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
