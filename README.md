# Set-up-Gitea-Database-and-Dron-by-one-click
Ansible playbook which installing Gitea, Database and Drone 

**Discription**

File /play_gitea_mysql is an ansible playbook which:
1) Installs Gitea 
2) Enables HTTPS for Gitea
3) Installs and configurs Mysql server 

File /play_drone.yaml is an ansible playbook which:
1) Installs and run Drone
2) Enables HTTPS for Drone
3) installs Drone Docker Runner 


Ansible dependency:
To make playbook works you have to install modules dependency on the your control node.
1) MySQLdb (Python 2.x)
2) PyMySQL (Python 2.7 and Python 3.x) or
3) mysql (command line binary)
4) mysqlclient (Python 3.5+) or
5) mysqldump (command line binary)


Environment preparation:

In file /play_gitea_mysql.yaml change this vars:

1) in role "enable_HTTPS" put your gites domain in var "domain" 
It needs to enable HTTPS for your Gitea server 

2) in role "install_mysqldb" put you giteas IP addres in var "giteas_ip" 
It needs to accept gitea to make request to database

In file /play_drone.yaml change this vars: 

1) in role "enable_HTTPS" put your Drones domain in var "domain" 
It needs to enable HTTPS for your Drone server

Drone Variables:

In file roles/install_drone/defaults/main.yaml - you have to change this vars:

1) DRONE_GITEA_SERVER: http://gitea-example.com
2) DRONE_GITEA_CLIENT_ID: 1234567890
3) DRONE_GITEA_CLIENT_SECRET: super-puper_secret
4) DRONE_RPC_SECRET: 1234567890
5) DRONE_SERVER_HOST: http://drone-example.com
6) DRONE_SERVER_PROTO: http
More about Drone environments ou can read here - https://docs.drone.io/server/referen

Drone Docker Runner Variables:

In file roles/install_drone_runner/defaults/main.yaml change this vars:

1) DRONE_RPC_PROTO: https
2) DRONE_RPC_HOST: drone.example.com
3) DRONE_RPC_SECRET: 123456789
4) DRONE_RUNNER_NAME: some name

Commands to run:
1) ansible-playbook -i inventory.ymal play_gitea_mysql.yaml
2) ansible-playbook -i inventory.ymal play_drone.yaml
