# Ansible
Ansible is an open-source automation tool for managing and configuring systems, deploying applications, and automating tasks using simple YAML scripts. It’s agentless, working over SSH, and simplifies infrastructure management.
Ansible can do 1. Provision (Creation). 2.Configuration management 3. Deployment(CI/CD) 4.network automation.

Puppet --> Chef --> Salt --> Ansible
For Puppet and Chef, need to install agent in servers.
We can write scripts in Playbooks which is in Yaml and it is agent less but need python as pre-requisite.
Here we need a Master/control Node and other are known as Manage nodes.
Inventry is a file where you define the manage nodes.

1. Password-less Authentication 

 With ssh key ```ssh-copy-id -f "-o identityFile <pem file>" ubuntu@IP```

with password ```ssh-copy-id ubuntu@IP```
But to run this the instance should be configured with password 
```sudo vim /etc/ssh/sshd_config.d/60-cloudimg-settings.conf```
then update authentication to yes 
In /etc/ssh/ there are files called ssh_config and sshd_config update the passwordauthentication as yes 
To set password ```sudo passwd ubuntu```
To restart the SSH ```sudo systemctl restart ssh```
Create inventry.ini file and configure your servers in format user@IP.

To run perticular commands on seleted group of servers ```ansible -i inventry.ini -m <module of command> -a <argument/command to run> <groupname>```

Here we have two type to give commands 1. Play Books(When you have many steps to run)/reusable 2. Adhoc commands (When you have simple steps)

# Example inventry File
```---
 - hosts: all
  become: true
  tasks:
    - name: Install apache httpd
      ansible.builtin.apt:
        name: apache2
        state: present
        update_cache: yes
    - name: Copy file with owner and permissions
      ansible.builtin.copy:
        src: index.html
        dest: /var/www/html
        owner: root
        group: root
        mode: '0644'```



