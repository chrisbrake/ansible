# Ansible
An area where I store my Ansible playbooks.

## Table of Contents
1. [Local setup](#localsetup)

## Local setup
Set up the system we will be running the playbooks from.  
Once it is complete you can add additional hosts into the file at ~/.ansible_hosts

If the ~/.ansible_hosts file does not exist, it will be initialized with a self entry for the local system.

    ansible-playbook local-setup.yml --ask-become

