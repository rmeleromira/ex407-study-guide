# EX407 Study Guide

### This study guide attempts to cover topics for study in the [Red Hat EX407 Red Hat Certificate of Expertise in Ansible Automation exam](https://www.redhat.com/en/services/training/ex407-red-hat-certificate-expertise-ansible-automation)

Got something to add? Make a Pull Request!

# **Disclaimer**

#### This guide does not divulge any information contained in the test, or style of the objectives. Merely publicly available information based on the wording of the objectives.


# Understand core components of Ansible
## Inventories
### Supply inventory with `-i` flag with commands

```ansible -i inventory -m shell -a “hostname"```

### [Can be set in ansible.cfg](http://docs.ansible.com/ansible/intro_configuration.html#inventory)
 
 `inventory = /etc/ansible/hosts`
### Static inventory

defined in ini style

```
[router]
hostname1 ansibe_host=192.168.1.1
[webserver]
hostname2 ansibe_host=192.168.1.2
[database]
hostname3 ansibe_host=192.168.1.3
[appserver]
hostname4 ansible_host=192.168.1.4
```


### Dynamic inventory

returns json
```
{
  "all": {
    "hosts": [
      "slaves_slave1"
    ]
  },
  "_meta": {
    "hostvars": {
      "slaves_slave1": {
        "ansible_host": "192.168.121.74"
      }
    }
  }
}
```

## Modules
[file](http://docs.ansible.com/ansible/file_module.html), [stat](http://docs.ansible.com/ansible/stat_module.html), [lineinfile](http://docs.ansible.com/ansible/lineinfile_module.html) etc
### file module example

#### Module usage

```
file: 
  path: /etc/config.cnf
  state: absent
```

#### Short hand

```
file: path=”/etc/config.cnf” state=”absent”
```

## Variables

### Variable can be used in inventories, playbooks, roles, defaults

## Facts

### Hostvars

### Setup module to retrieve facts

### Debug module to verify facts

## Plays

## Individual roles

## Playbooks

File with a collection of roles/plays

## Configuration files

/etc/ansible/ansible.cfg

# Run ad-hoc Ansible commands
```
ansible [groupname] [-i inventory-file] [-m module] [-a arguments]
ansible all -i inventory -m shell -a “hostname”
```

# Use both static and dynamic inventories to define groups of hosts

## Static inventory take single hosts by line or ini format

Dynamic inventories return information from outside sources like AWS to gather facts about the inventory

## Example for creating dynamic inventories

[https://www.jeffgeerling.com/blog/creating-custom-dynamic-inventories-ansible](https://www.jeffgeerling.com/blog/creating-custom-dynamic-inventories-ansible)

# Utilize an existing dynamic inventory script
./inventory.py
{}
./inventory.py --list 
{"all": {"hosts": ["slaves_slave2", "slaves_slave3", "slaves_slave4", "slaves_slave1", "slaves_slave5"]}, "_meta": {"hostvars": {"slaves_slave5": {"ansible_host": "192.168.121.32"}, "slaves_slave4": {"ansible_host": "192.168.121.29"}, "slaves_slave1": {"ansible_host": "192.168.121.218"}, "slaves_slave3": {"ansible_host": "192.168.121.34"}, "slaves_slave2": {"ansible_host": "192.168.121.119"}}}}
./inventory.py --host
{
  "all": {
    "hosts": [
      "slaves_slave1"
    ]
  },
  "_meta": {
    "hostvars": {
      "slaves_slave1": {
        "ansible_host": "192.168.121.218"
      }
    }
  }
}

# Create Ansible plays and playbooks

# Know how to work with commonly used Ansible modules

# Use variables to retrieve the results of running a commands
# Use conditionals to control play execution
# Configure error handling

[fail module](http://docs.ansible.com/ansible/fail_module.html)

```
- fail:
    msg: "The system may not be provisioned according to the CMDB status."
  when: cmdb_status != "to-be-staged"
```

# Create playbooks to configure systems to a specified state
# Selectively run specific tasks in playbooks using tags
# Create and use templates to create customized configuration files
# Work with Ansible variables and facts
# Create and work with roles
# Download roles from an Ansible Galaxy and use them
# Manage parallelism
# Use Ansible Vault in playbooks to protect sensitive data
# Install Ansible Tower and use it to manage systems
# Use provided documentation to look up specific information about Ansible modules and commands
## [List of modules](http://docs.ansible.com/ansible/modules_by_category.html)
[Module example](http://docs.ansible.com/ansible/stat_module.html)
