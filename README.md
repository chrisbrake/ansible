# Ansible
An area where I store my Ansible playbooks.

## Table of Contents
1. [mDNS](#mdns)
1. [ssh](#ssh)
1. [sudo](#sudo)
1. [laptop-server](#laptop-server)
1. [Docker](#docker)
1. [Codecs](#codecs)


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
    
## laptop-server
Configures the power management settings on a laptop to make it more usable as a home server.

    ansible-playbook -i '192.168.0.0,' laptop-server.yml

## Docker
This is intended to get Docker installed and running.  With the active user able to administer the system without needing to elevate privileges.
* Installs and enables Docker.
* Creates a docker group, and adds that groups access to the ansible user.


## Codecs
This is intended to install additional video/audio codecs.  Because this requires adding additional repos, it currently only supports Fedora.
* Enables additional repos.
* Installs codec software.
