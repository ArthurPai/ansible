docker-mongodb
=======

This Ansible playbook will run a MongoDB replica set using Docker containers. You will need to edit 'hosts' file to include hostname (or IP) for the primary and secondary server nodes. Then edit 'group_vars/all' file for Docker and MongoDB related configuration settings. 

### This Ansible playbook will:

1. Install Docker
2. Download MongoDB base image from public Docker repo
3. Customize MongoDB configuration file
4. Run MongoDB image
5. Initialize MongoDB replica set
Done.

### Recommended setup:
```
1 x Ansiblehost (minimum resource needed)
1 x MongoDB primary server
N x MongoDB secondary servers (should have at least two, this setup does not support arbiter)
```

### Usage (Linux):

1) Install Ansible
```
> yum install -y ansible
```
2) Install Git
```
> yum install -y git
```
3) Create repo directory
```
> mkdir repo
> cd repo
```
4) Fork this proj to your own git repo, or git pull from parent directory
```
> git pull https://github.com/gisgit/ansible.git
> cd ansible/docker-mongodb
```
5) Edit 'hosts' file and enter hostname or ip for primary and secondary servers
```
> vi hosts
```
6) (optional) Edit 'global_vars/all' to configure settings for Docker and MongoDB
```
> vi global_vars/all
```
7) (optional) Ansible uses ssh to operate on client machines. If haven't done so, create ssh key and build ssh authentication between machines.
```
> ssh-keygen
(password-less rsa key should do)
> ssh-copy-id -i .ssh/id_rsa.pub <username>@<client-hostname>
(repeat ssh-copy-id for all client machines)
```
8) Run Ansible playbook
```
> ansible-playbook -i hosts demo.yml --ask-sudo-pass
```
Done. To verify successful roll out of MongoDB replica set, ssh to a client machine and type
```
> mongo
(enter mongo shell at default port 27017)
> rs.status()
(print replica set status)
```