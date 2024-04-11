# Ansible-Server-Management-Project

#Procedure :

1. Launch the ansible-master-key EC2 Instance.
2. Create a key-pair that will be used for all the instances to which we have to connect.
3. Create the 3-server (like server-1 ,server-2 and server-3)

4. Add a repository for ansible
$ sudo apt-add-repository ppa:ansible/ansible (not mandatory)

# Installation of Ansible:

# Update Package Lists:
$ sudo apt update

# install Ansible:
$ sudo apt install ansible

# Verify Installation:
# Check Ansible version to verify installation:
$ ansible --version

# Edit the Ansible inventory file (hosts):
By editing this file, you can specify the IP addresses or hostnames of your servers, configure SSH settings, define server groups, and more. 
$ sudo nano /etc/ansible/hosts

# after opening the file.
# Create a new group for your own servers using :
[servers]
server_1 ansible_host=server1_local_IP
server_2 ansible_host=server1_local_IP
server_3 ansible_host=server1_local_IP

# you can also make a prod server for server_3 by making another group:(removed it from normal servers)
[prdserver]
server_3 ansible_host=server1_local_IP

# create a directory for connecting the all the server by using private key (.pem ):
$ mkdir keys
$ cd keys

# We have to tranfer the pem file from local to server:
1. Open the ansible-master instances
2. Go to the SSH client copy the example :
    ssh -i "ansible-master-key.pem" ubuntu@ec2-13-232-125-157.ap-south-1.compute.amazonaws.com

3. Set Permissions for the Private Key:
# Set appropriate permissions for the private key file in WSL to ensure it's secure:
$ chmod 400 /path/to/ansible-master-key.pem

$ scp C:\Users\YourUsername\Documents\example.txt username@hostname:/home/username/keys

# Remove permissions for BUILTIN\Users group
icacls "C:\Users\mahig\Desktop\ansible-master-key.pem" /remove BUILTIN\Users

# Set permissions to read and write for the current user onl
$ icacls "C:\Users\mahig\Desktop\ansible-master-key.pem" /inheritance:r /grant:r "%USERNAME%:(R,W)"

# Verify permissions
$ icacls "C:\Users\mahig\Desktop\ansible-master-key.pem"

# All servers used private key by using:
change in : $ sudo nano /etc/ansible/hosts

[servers:vars]
ansible_ssh_private_key_file=Path of the server pem file
ansible_python_interpreter=/usr/bin/python3 (for every server python3 will be installed)
ansible_user=ubuntu

# Run to check ping or connectivity of the all the servers
$ ansible servers -m ping

# Update all the servers using :
$ ansible servers -a"sudo apt update"








