ansible_role_ssh_hosts_config
=========

Manage SSH hosts config file. Add new hosts, with custom names, ports

Requirements
------------

This role requires Ansible 2.0 or higher and platform requirements are listed
in the metadata file.

Role Variables
--------------
```yaml
ssh_hosts_config_identity_file: ~/.ssh/id_rsa
ssh_hosts_config:
  - name: host1
    hostname: foo.bar
    ssh_port: 22
  - name: host2
    hostname: baz.boo
    ssh_port: 2222
```

Example Playbook
----------------

```yaml
- name: provision servers
  hosts: all
  become: true
  roles:
    - { role: 'brnck.ansible_role_ssh_hosts_config', tags: 'ssh-hosts-config' }
  vars:
    ssh_hosts_config_identity_file: ~/.ssh/id_rsa
    ssh_hosts_config:
      - name: host1
        hostname: foo.bar
        ssh_port: 22
      - name: host2
        hostname: baz.boo
        ssh_port: 2222
```

Install
-------

```sh
ansible-galaxy install brnck.ansible_role_ssh_hosts_config
```

Tests
------------

```sh
docker build -t test-ansible-ssh-hosts-config-debian8 -f tests/Dockerfile_debian8 --force-rm .
docker build -t test-ansible-ssh-hosts-config-debian9 -f tests/Dockerfile_debian9 --force-rm .
docker build -t test-ansible-ssh-hosts-config-ubuntu16 -f tests/Dockerfile_ubuntu16 --force-rm .
docker build -t test-ansible-ssh-hosts-config-ubuntu18 -f tests/Dockerfile_ubuntu18 --force-rm .
```
