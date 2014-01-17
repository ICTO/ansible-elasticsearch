# Readme

## Description

*ansible-elasticsearch* is an [Ansible](http://ansible.cc) role.
The role contains tasks to install Elasticsearch, with the Paramedic dashboard.

## Provides

1. Elasticsearch
2. Paramedic dashboard

## Requires

1. Ansible 1.4 or higher
2. Debian 7.3 (other deb-based distros should work too)
3. Vagrant (optional)

## Usage

### Get the code

```bash
$ git clone git@github.com:ICTO/ansible-elasticsearch.git
```

### Create the playbook file

```
---
- name: Elasticsearch
  hosts: elasticsearch
  roles:
    - ansible-elasticsearch
```

### Run the playbook

Use *ansible.host* as inventory. Run the playbook only for the remote host *elasticsearch*. Use *vagrant* as the SSH user to connect to the remote host. *-k* enables the SSH password prompt.

```bash
$ ansible-playbook -k -i ansible.host elasticsearch.yml -u vagrant
```

### Example output

```
```