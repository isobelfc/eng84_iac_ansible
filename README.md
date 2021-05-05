# Infrastructure as Code

- method to provision and manage IT infrastructure through the use of  machine-readable definition files (i.e. source code)
- on premises or cloud
- mutable or immutable

## Benefits
- speed
- simplicity
- configuration consistency
- risk minimisation
- increased efficiency
- cost savings

## Best Practices
- codify everything
- document as little as possible
- maintain version control
- continuously test, integrate, deploy
- make infrastructure code modular
- make infrastructure immutable when possible

## Two Parts
- configuration management
    - tools responsible for provisioning and maintaining the state of your systems
    - e.g. Chef, Puppet, Ansible
- orchestration
    - talk to the cloud to pull templates together into the architecture
    - e.g. CloudFormation (AWS), Ansible, Terraform
    
## Benefits of Ansible
- uses YAML, which is human-readable
- agentless - do not need to install Ansible on agent nodes, only the master
    - this makes the agent nodes lightweight
- uses SSH to connect to any other server
- growing of multi-cloud and hybrid cloud - 
- common platform
- integrates with other tools, e.g. Jenkins, Docker


- command to SSH into app and db from controller is `ssh vagrant@ip`

## Adhoc Commands
- adhoc vs playbook
  - playbooks contain series of commands to configure, deploy and orchestrate, and are useful for repeating tasks in the same way
  - adhoc commands are run directly in the command line, and are useful for rarely used commands
- need to add hosts to /etc/ansible/hosts
```
[web]
[web]
ip ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
```
- can then use `ansible web -m ping`
- can also use `ping ip`
- `ansible web -a "command"` gets information of other machines from the controller, e.g. `uname`, `date`
- `ansible db -m shell -a "uptime"` to find uptime of the db server
- `ansible all -a "sudo apt-get update"` to update all packages
- `ansible all -a "sudo apt-get upgrade"` to upgrade