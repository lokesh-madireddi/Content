# Ansible
Ansible is an open-source automation tool for managing and configuring systems, deploying applications, and automating tasks using simple YAML scripts. It’s agentless, working over SSH, and simplifies infrastructure management.
Ansible can do 1. Provision (Creation). 2.Configuration management 3. Deployment(CI/CD) 4.network automation.

Puppet --> Chef --> Salt --> Ansible
For Puppet and Chef, need to install agent in servers.
We can write scripts in Playbooks which is in Yaml and it is agent less but need python as pre-requisite.
Here we need a Master/control Node and other are known as Manage nodes.

Inventry is a file where you define the manage nodes.

