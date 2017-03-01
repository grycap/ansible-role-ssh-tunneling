[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

SSH Tunneling
=============

Ansible role to create SSH tunnels between two hosts. It is used in EC3 to create hybrid clusters.
This role allows connectivity between frontend and working nodes when frontend is behind a firewall by using SSH tunnels. Once established the tunnels, working nodes redirect traffic to the frontend throw the tunnel. For that it is installed redsocks and inserted some rules in IPTables. See: http://darkk.net.ru/redsocks/
Notice that only nodes that are deployed outside the Cloud provider that has deployed the front-end, need to configure SSH tunnels to connect with the cluster.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	ssh_tunnels_node: "front"
	front_ip: "127.0.0.1"
	front_ports: ""

Example Playbook
----------------
```
  - hosts: server
  roles:
  - { role: 'grycap.ssh-tunneling', ssh_tunnels_node: 'front'}
```
```
  - hosts: external_client
  roles:
  - { role: 'grycap.ssh-tunneling', ssh_tunnels_node: 'wn'}
```

Contributing to the role
========================
In order to keep the code clean, pushing changes to the master branch has been disabled. If you want to contribute, you have to create a branch, upload your changes and then create a pull request.  
Thanks