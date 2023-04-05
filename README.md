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
  - name: "group1"
    host_groups: "server1" # if you want to create a group on particular hosts
  - name: "group2"
    host_groups: "all" # if you want to create a group on all hosts

accounts_manage_users:
  - username: "user"
    groups: "group_1, group_2" # if you want to create a user on particular hosts
    ssh_keys: "ssh-rsa AAAAB3NzaC1yc2EAAAA"
    state: absent
    host_groups: "all"
  - username: "user2"
    groups: "group_1" # if you want to create a user on all hosts
    ssh_keys: "ssh-rsa AAAAB3NzaC1yc2EAAAA"
    host_groups: "server1"

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
