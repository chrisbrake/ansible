# ansible
An area where I store my Ansible playbooks.
These will be set up for Linux systems.  Intending to stay as distro agnostic as possible.

# Table of Contents
1. [Bootstrap](#bootstrap)
2. [Docker](#docker)
2. [Codecs](#codecs)


## Bootstrap
This is intended to get a node off the ground.  Allowing you to more easily run further playbooks.
* Installs and enables Avahi, and SSH.
* Disables root login, and password authentication for ssh.
* Adds your user with sudo permissions (no prompt), and your public key installed.

In order to use these files effectively you will need to make a Ansible vault called secrets.yml to store  variables with your private information.  
For instructions on how to make one of these see [Ansible's documentation](https://docs.ansible.com/ansible/2.4/vault.html#creating-encrypted-files).
* ansible_ssh_user - The user to log into the remote systems as, for ease of use this should be the same name as the user you will run the playbooks as.
* ssh_key_location - The location of the ssh public key(s) to install.

Recommended to run locally, so it can set up your Ansible user.  Call it as: 

    ansible-playbook --ask-vault-pass --connection=local -i 'localhost,' bootstrap.yml


## Docker
This is intended to get Docker installed and running.  With the active user able to administer the system without needing to elevate privileges.
* Installs and enables Docker.
* Creates a docker group, and adds that groups access to the ansible user.


## Codecs
This is intended to install additional video/audio codecs.  Because this requires adding additional repos, it currently only supports Fedora.
* Enables additional repos.
* Installs codec software.

## mDNS
This is intended to set up mDNS on the target system so it find and be found using it's hostname.
Because of some specifics around the firewall setup in ansible you'll need to do this explicitly in python 3.
     
     ansible-playbook --connection=local -i 'localhost,' mdns.yml  --ask-become-pass -e "ansible_python_interpreter=/usr/bin/python3"
     
## ssh
Configures ssh to accept the key from your home directory, turns off root log in and root login.

    ansible-playbook -i '192.168.0.0,' ssh.yml  --ask-become-pass  --ask-pass
    
## sudo
Configures the current user to not be prompted for sudo commands

    ansible-playbook -i '192.168.0.0,' sudo.yml  --ask-become-pass
