# aws-cloud-projects
1) login to aws management console .
2) In search console type "ec2" and search.
3) Instance >  Go to launch Instance > namethe instance >Select ubuntu "AMI" image with free tire intance type "t2.micro" .
4) security group > allow http ,ssh,https "rules"  to your instance.
5) preview config > Launch Instance.
6) once the instance is launched > create an Elastic Ip "note: Elastic ip addres doesnt add to cost until it is attached with any of the instances".
7) attach the elastic ip with ec2 "the elastic ip should be punlic ipv4 address".
8) copy the ip public ipv4 adrress from running instance.

Connect to the EC2 Instance:

Use an SSH client (e.g., PuTTY on Windows or Terminal on macOS/Linux) to connect to your EC2 instance using the public IP address or DNS name.
Example command: ssh -i your-key.pem ubuntu@your-instance-public-ip
Install LAMP Stack (Linux, Apache, MySQL, PHP):

Update package lists: sudo apt update
Install Apache: sudo apt install apache2
Install MySQL: sudo apt install mysql-server
Secure MySQL installation: sudo mysql_secure_installation
Install PHP and required modules: sudo apt install php libapache2-mod-php php-mysql
Create MySQL Database and User:

Log in to MySQL as the root user: sudo mysql -u root -p
Create a database for WordPress: CREATE DATABASE wordpress;
Create a MySQL user and grant privileges:
sql
Copy code
CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';
FLUSH PRIVILEGES;
Download and Configure WordPress:

Download the latest WordPress release: wget https://wordpress.org/latest.tar.gz
Extract the archive: tar -zxvf latest.tar.gz
Move WordPress files to Apache root directory: sudo mv wordpress/* /var/www/html/
Set appropriate permissions: sudo chown -R www-data:www-data /var/www/html/
Rename the sample configuration file: sudo mv /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
Edit wp-config.php file to add MySQL database details:
sql
Copy code
define('DB_NAME', 'wordpress');
define('DB_USER', 'wordpressuser');
define('DB_PASSWORD', 'yourpassword');
Configure Apache for WordPress:

Enable rewrite module: sudo a2enmod rewrite
Restart Apache: sudo systemctl restart apache2
