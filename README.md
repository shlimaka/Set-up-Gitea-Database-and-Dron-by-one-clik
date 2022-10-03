# Set-up-Gitea-Database-and-Dron-by-one-clik
Ansible playbook which installing Gitea, Database and Drone 

Ansible dependency:
To make playbook works you have to install modules dependency on the your control node.
1) MySQLdb (Python 2.x)
2) PyMySQL (Python 2.7 and Python 3.x) or
3) mysql (command line binary)
4) mysqlclient (Python 3.5+) or
5) mysqldump (command line binary)

Environment preparation:

Mysql Variables:
In file roles/install_mysqldb/defaults/main.yaml - you have to change this vars:

1) giteas_ip: 123.456.78.9 - to your gitea ip
2) password_for_gitea_db_user: gitea - to your mysql users password

Drone Variables:
In file roles/install_drone/defaults/main.yaml - you have to change this vars:

1) DRONE_GITEA_SERVER: http://gitea-example.com
2) DRONE_GITEA_CLIENT_ID: 1234567890
3) DRONE_GITEA_CLIENT_SECRET: super-puper_secret
4) DRONE_RPC_SECRET: 1234567890
5) DRONE_SERVER_HOST: http://drone-example.com
6) DRONE_SERVER_PROTO: http

More about Drone environments you can read here - https://docs.drone.io/server/reference/

Enable_HTTPS Variables:
In fiel roles/enable_HTTPS/defaults/main.yaml - change this vars:

1) domain: example_domain.com - change it to your giteas domain
