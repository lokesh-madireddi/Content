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