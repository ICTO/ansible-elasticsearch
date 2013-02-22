# Readme

## Description

*ansible-elasticsearch* is an [Ansible](http://ansible.cc) playbook.
The playbook contains tasks to install Elasticsearch server, with optionally the Paramedic dashboard.

## Requirements

### Ansible

Everything is documented on the [Ansible](http://ansible.cc/docs/gettingstarted.html) site...

### Supported platforms

Playbook tested on *Debian-7.0-b4-amd64*, probably works on other Debian versions too. Heavily depends on *apt*, sorry CentOS users...

## Usage

### Get the code

```bash
$ git clone git@github.ugent.be:tberton/ansible-elasticsearch.git
```

### Create a host file

Following example make ansible aware of the Vagrant box reachable on localhost port 2222.

```bash
$ vi ansible.host
```

with

```
[vagrant]
127.0.0.1 ansible_ssh_port=2222
```

### Create host specific variables

Make the host_vars directory where *ansible.host* file is located.

```bash
$ mkdir host_vars
```

Create a file in the newly created directory matching your host.

```bash
$ cd host_vars
$ vi 127.0.0.1
```

with

```
---
with_redmon: true
```

### Example output

```
SSH password: 

PLAY [vagrant] ********************* 

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

### Run the playbook

Use *ansible.host* as inventory. Run the playbook only for the remote host *vagrant*. Use *vagrant* as the SSH user to connect to the remote host. *-k* enables the SSH password prompt.

```bash
$ ansible-playbook -k -i ansible.host ansible-elasticsearch/setup.yml --extra-vars="hosts=vagrant user=vagrant"
```

## Docs and contact

Read more on the Wiki pages about how this playbook works.

http://icto.ugent.be
