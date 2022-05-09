WordPress on LEMP (Linux, Nginx, MySQL, PHP) on Ubuntu 22.04 LTS

I am starting my DevOps jurney, as I have learnt how to setup a WordPress site on Linux Server, I wanted to automate the proces using ansible.
This ansible playbook help me deploy WordPress and LEMP environment fast to the new bare metal Linux server.
With this project I have learned a little bit about ansible, CM, Nginx and Linux in general.
This is only a POC, this is not production ready server configuration.

Options:
- mysql_root_password: The desired password for the root MySQL.
- mysql_db: The name of the MySQL database that should be created for WordPress.
- mysql_user: The name of the MySQL user that should be created for WordPress.
- mysql_password: The password for the new MySQL user.
- http_host: Your domain name.
- http_conf: The name of the configuration file that will be created within Nginx.
- http_port: HTTP port for this virtual host, where 80 is the default.

Usage:
1. Obratin the playbook
git clone 
cd ansible-projects/wp-lemp-ubuntu2204

2. Customize options
nano vars/default.yml

MySQL setings
- mysql_root_password: "mysqlrootpassword"
- mysql_db: "wordpress"
- mysql_user: "wordpress"
- mysql_password: "password"
HTTP setings
- http_host: "hostname"
- http_conf: "wordpress.conf"
- http_port: "80"

3. Run the playbook
ansible-playbook playbook.yml -l [target] -u [sudo user on target] --extra-vars 'ansible_become_pass=[sudo user password]'
