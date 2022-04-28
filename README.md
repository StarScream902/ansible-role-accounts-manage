Accounts namage role
=========

A simple Ansible role for accounts and groups to manage, also it can manage sudoers rules

Requirements
------------

NO

Role Variables
--------------

```yaml
accounts_manage_groups:
- "group1"
- "group2"

accounts_manage_users:
- username: "user"
  groups: "group_1, group_2"
  ssh_keys: "ssh-rsa AAAAB3NzaC1yc2EAAAA"

accounts_manage_sudoers: |
  {% if ansible_os_family == "Debian" %}
  %adm        ALL=(ALL:ALL)       NOPASSWD: ALL
  {% endif %}
  {% if ansible_os_family == "RedHat" %}
  %wheel        ALL=(ALL:ALL)       NOPASSWD: ALL
  {% endif %}

accounts_manage_sudoers_rules:
- name: ""
  rule: |
    some rule
```

Dependencies
------------

NO

Example Playbook
----------------

```yaml
---
- name: accounts manage
  hosts: all
  become: true

  roles:
    - role: accounts-manage
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
