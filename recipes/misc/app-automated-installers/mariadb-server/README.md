# AUTOMATED MARIADB 10.1 INSTALLER FOR CENTOS7

This script (for user_data on cloud system or to be run manually) will install mariadb 10.1 from oficial MariaDB repos for Centos 7.

If the script find a secondary free disk/volume, it will use it for the database storage. In such case, the volume will be mounted on "/var/mariadb-storage". The "/var/lib/mysql" directory will be moved to "/var/mariadb-storage/mysql", then symlinked back to /var/lib/mysql.

The credentials are autogenerated and later stored on the file /root/mariabd-access-info.txt. Also, the file /root/.my.cnf will be configured with the database root user credentials in order to let the "mysql" command to connect without including user/password on the mysql command call.

Most of the tasks performed by this script will be logged to the file "/var/log/mariadbserver-automated-installer.log"

Please note that this script will disable selinux.

# PHPMYADMIN

PHPMyAdmin is included as an option controlled by the variable "phpmyadmin" at the begining of the script. By default, is set to "yes" (phpmyadmin and required dependencies will be installed). Setting this to "no" or any other value different to "yes" will make the script to not install phpmyadmin.


# FIREWALLD

Firewalld will be installed and configured. The only ports to open will be:

- 22 tcp (ssh).
- 3306 tcp (mariadb).
- 80 and 443 tcp (http/https) "only" if phpmyadmin is installed.


# GENERAL REQUIREMENTS:

This script will fail if the following requirements are not meet:

- Operating System: Centos 7.
- Architecture: x86_64/amd64.
- INSTALLED RAM: 1024Mb (1GB).
- CPU: 1 Core/Thread.
- FREE DISK SPACE: 5GB.
