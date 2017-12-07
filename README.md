# ansible
An area where I store my Ansible playbooks.
These will be set up for Linux systems.  Intending to stay as distro agnostic as possible.

# Table of Contents
1. [Introduction](#introduction)
2. [Bootstrap](#bootstrap)

## Introduction
In order to use these files effectively you will need to make a Ansible vault to store information.  
For instructions on how to make one of these see [Ansible's documentation](https://docs.ansible.com/ansible/2.4/vault.html#creating-encrypted-files).
The recommended name for this is secrets.yml and it should contain the following variables.
* ansible_user
* ansible_password
* ssh_key_location

## Bootstrap
This is intended to get a node off the ground.  
* Installs and enables Avahi, and SSH.
* Disables root login, and password authentication for ssh.
* Adds your user with sudo permissions, and your public key installed.
