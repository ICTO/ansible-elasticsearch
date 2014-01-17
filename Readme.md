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
SSH password: 

PLAY [Elasticsearch] ********************************************************** 

GATHERING FACTS *************************************************************** 
ok: [127.0.0.1]

TASK: [ansible-elasticsearch | Install Elasticsearch dependencies] ************ 
ok: [127.0.0.1] => (item=openjdk-6-jre)
ok: [127.0.0.1] => (item=openjdk-6-jdk)

TASK: [ansible-elasticsearch | Fetch Elasticsearch] *************************** 
ok: [127.0.0.1]

TASK: [ansible-elasticsearch | Install Elasticsearch package] ***************** 
skipping: [127.0.0.1]

TASK: [ansible-elasticsearch | Ensure Elasticsearch is running] *************** 
ok: [127.0.0.1]

TASK: [ansible-elasticsearch | Install Paramedic dashboard] ******************* 
skipping: [127.0.0.1]

PLAY RECAP ******************************************************************** 
127.0.0.1                  : ok=4    changed=0    unreachable=0    failed=0  
```