# Ansible-Server-Management-Project

Procedure :

1. Launch the ansible-master-key EC2 Instance.
2. Create a key-pair that will be used for all the instances to which we have to connect.
3. Create the 3-server (like server-1 ,server-2 and server-3)

4. Add a repository for ansible
$ sudo apt-add-repository ppa:ansible/ansible (not mandatory)

Installation of Ansible:

Update Package Lists:
$ sudo apt update

install Ansible:
$ sudo apt install ansible

Verify Installation:
Check Ansible version to verify installation:
$ ansible --version

Edit the Ansible inventory file (hosts):
By editing this file, you can specify the IP addresses or hostnames of your servers, configure SSH settings, define server groups, and more. 
$ sudo nano /etc/ansible/hosts

Create a new group for your own servers using :
[servers]
server_1 ansible_host=server1_local_IP
server_2 ansible_host=server1_local_IP
server_3 ansible_host=server1_local_IP






