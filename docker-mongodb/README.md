This Ansible playbook will run a MongoDB replica set using Docker containers. You will need to edit 'hosts' file to include hostname (or IP) for the primary and secondary server nodes. Then edit 'group_vars/all' file for Docker and MongoDB related configuration settings. 

This Ansible playbook will:
1. Install Docker
2. Download MongoDB base image from public Docker repo
3. Customize MongoDB configuration file
4. Run MongoDB image
5. Initialize MongoDB replica set
Done.