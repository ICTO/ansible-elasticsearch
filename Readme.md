# Readme

## Description

*ansible-elasticsearch* is an [Ansible](http://ansible.cc) playbook.
The playbook contains tasks to install Elasticsearch server, with optionally the Paramedic dashboard.

## Requirements

### Ansible

Everything you should know about Ansible is documented on the [Ansible](http://ansible.cc/docs/gettingstarted.html) site...

### Supported platforms

#### Debian wheezy

Playbook tested on *Debian-7.0-b4-amd64*, probably works on other Debian versions too. Heavily depends on *apt*, sorry CentOS users...

#### Ansible >= 1.0

Any Ansible version >= 1.0 should work. If not, please use the issue tracker to report any bugs.

## Usage

### Get the code

```bash
$ git clone git@github.ugent.be:tberton/ansible-elasticsearch.git
```

### Create an Ansible inventory file

Following example makes Ansible aware of a box reachable through SSH on 127.0.0.1, port 2222.

```bash
$ vi ansible.host
```

with

```
[elasticsearch]
127.0.0.1 ansible_ssh_port=2222

[elasticsearch:vars]
with_redmon=True
```

The *ansible-elasticsearch* playbook is only executed for the host/group *elasticsearch*.

### Run the playbook

Use *ansible.host* as inventory. Run the playbook only for the remote host *elasticsearch*. Use *vagrant* as the SSH user to connect to the remote host. *-k* enables the SSH password prompt.

```bash
$ ansible-playbook -k -i ansible.host ansible-elasticsearch/setup.yml --extra-vars="user=vagrant"
```

### Example output

```
SSH password: 

PLAY [elasticsearch] ********************* 

GATHERING FACTS ********************* 
ok: [127.0.0.1]

TASK: [Install Elasticsearch dependencies] ********************* 
ok: [127.0.0.1] => (item=openjdk-6-jre,openjdk-6-jdk)

TASK: [Fetch Elasticsearch: http://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-0.20.5.deb] ********************* 
ok: [127.0.0.1]

TASK: [Install Elasticsearch package: elasticsearch-0.20.5.deb] ********************* 
skipping: [127.0.0.1]

TASK: [Add JAVA_HOME to Elasticsearch init script] ********************* 
ok: [127.0.0.1]

TASK: [Ensure Elasticsearch is running] ********************* 
ok: [127.0.0.1]

TASK: [Install Paramedic dashboard] ********************* 
changed: [127.0.0.1]

PLAY RECAP ********************* 
127.0.0.1                   : ok=6    changed=1    unreachable=0    failed=0
```

## Docs and contact

Read more on the Wiki pages about how this playbook works.

http://icto.ugent.be
