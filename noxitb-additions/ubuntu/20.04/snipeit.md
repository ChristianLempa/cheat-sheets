[Snipe-IT](https://snipeitapp.com/) was made for IT asset management, to enable IT departments to track who has which laptop, when it was purchased, which software licenses and accessories are available, and so on. Snipe-IT is a open-source IT asset management and it eliminates the need for complex IT asset tracking spreadsheets.

#### Prerequisites

- An Ubuntu 20.04 installed dedicated server or KVM VPS
- A root user access or normal user with administrative privileges.

### Install Snipe-IT on Ubuntu 20.04

#### 1\. Update the server and install dependencies:

> \# apt update -y
>
> \# apt upgrade -y

Install unzip dependency

> \# apt-get install unzip -y

#### 2\. Install Apache webserver

> \# apt install apache2 -y

After the installation, start and enable apache2 service using following command:

> \# systemctl start apache2 && systemctl enable apache2

In case, you enabled firewall and firewall block requests of the apache web server, open a port in the firewall.

> \# ufw allow 80/tcp
>
> \# ufw allow 443/tcp
>
> \# ufw reload

Now, let’s verify the Apache installation. Open browser and test default page.

> http://\[SERVER IP\]

Enable Apache’s *mod_rewrite* module. Snipe-IT requires this extension to rewrite URLs more cleanly.

> \# sudo a2enmod rewrite

Restart your Apache web server to apply the changes.

> \# systemctl restart apache2

#### 3\. Install MariaDB

> \# apt install mariadb-server mariadb-client -y

Start and enable mariadb service using following command:

> \# systemctl start mariadb && systemctl enable mariadb

The default configuration of the MariaDB will not be secured. Let’s secured the installation using the following command:

> \# mysql_secure_installation

Once the script gets executed, it will ask multiple questions.

It will ask you to enter the current password for root (enter for none):

Then enter yes/y to the following security questions:

> Set a root password? \[Y/n\]: y  
> Remove anonymous users? : y  
> Disallow root login remotely? : y  
> Remove test database and access to it? : y  
> Reload privilege tables now? : y

#### 4\. Install PHP and PHP Composer

Here we are installing the default PHP version 7.4 and other modules for web deployments using the following command:

> \# apt install php php-bcmath php-bz2 php-intl php-gd php-mbstring php-mysql php-zip php-opcache php-pdo php-calendar php-ctype php-exif php-ffi php-fileinfo php-ftp php-iconv php-intl php-json php-mysqli php-phar php-posix php-readline php-shmop php-sockets php-sysvmsg php-sysvsem php-sysvshm php-tokenizer php-curl php-ldap -y

Install PHP Composer, which is a PHP dependency management tool to install and update libraries in your Snipe-IT.

Download the Composer installer.

> \# curl -sS https://getcomposer.org/installer | php

Move the composer.phar executable to /usr/local/bin/.

> \# mv composer.phar /usr/local/bin/composer

#### 5\. Create a Database

Create a database and database user for Snipe-IT. First login into MySQL/MariaDB as a root user.

> \# mysql -u root -p

Run following commands to perform this task:

> CREATE DATABASE snipe_it;  
> CREATE USER ‘snipe_it_user’@’localhost’ IDENTIFIED BY ‘EXAMPLE_PASSWORD’;  
> GRANT ALL PRIVILEGES ON snipe_it.\* TO ‘snipe_it_user’@’localhost’;  
> FLUSH PRIVILEGES;  
> EXIT;

Note: Replace _snipe_it_user_ to your choice username and replace _EXAMPLE_PASSWORD_ to you choice password.

#### 6\. Install Snipe-IT

Navigate to the root directory of your web server.

> \# cd /var/www/

Use git to clone the latest Snipe-IT repository from the https://github.com/snipe/snipe-it URL and copy the downloaded files to a snipe-it directory.

> \# git clone https://github.com/snipe/snipe-it snipe-it

Switch to the snipe-it directory.

> \# cd /var/www/snipe-it

Snipe-IT ships with a sample configuration file. Copy it to /var/www/snipe-it/.env.

> \# cp /var/www/snipe-it/.env.example /var/www/snipe-it/.env

Edit the configuration file.

> \# nano /var/www/snipe-it/.env

In the Snipe-IT configuration file, locate these settings.

> APP_URL=null  
> APP_TIMEZONE=’UTC’

Set APP_URL to your server’s Fully Qualified Domain Name, or it’s public IP address. If you use a time zone other than UTC, change the timezone to a PHP-supported timezone, and enclose it in single quotes.

> APP_URL=example.com  
> APP_TIMEZONE=’America/New_York’

Locate these settings.

> DB_DATABASE=null  
> DB_USERNAME=null  
> DB_PASSWORD=null

Change those values to the database information you set up in Step 3.

> DB_DATABASE=snipe_it  
> DB_USERNAME=snipe_it_user  
> DB_PASSWORD=EXAMPLE_PASSWORD

Save and close the file.

Set the correct ownership and permission for the Snipe-IT data directory.

> \# chown -R www-data:www-data /var/www/snipe-it  
> \# chmod -R 755 /var/www/snipe-it

Install the Snipe-IT dependencies with Composer. You’ll receive a warning not to run this as root on each command. It’s okay to continue as root for the Snipe-IT install, so type yes and hit ENTER.

> \# composer update –no-plugins –no-scripts  
> \# composer install –no-dev –prefer-source –no-plugins –no-scripts

Once the Composer finishes running, generate a Laravel APP_Key value in the /var/www/snipe-it/.env configuration file you created earlier. Type yes and hit ENTER when prompted to continue.

> \# php artisan key:generate

#### 7\. Create a Virtual Host File

First we’ll disable default Apacheconf file and create new vhost conf file.

Disable the default Apache configuration file.

> \# a2dissite 000-default.conf

Create a new Apache configuration file.

> \# nano /etc/apache2/sites-available/snipe-it.conf

Paste the information below and replace example.com with your server’s domain name or public IP address.

> <VirtualHost \*:80>  
> ServerName example.com  
> DocumentRoot /var/www/snipe-it/public  
> <Directory /var/www/snipe-it/public>  
> Options Indexes FollowSymLinks MultiViews  
> AllowOverride All  
> Order allow,deny  
> allow from all  
> </Directory>  
> </VirtualHost>

Save and exit the file.

Enable your new configuration file.

> \# a2ensite snipe-it.conf

Restart your Apache web server to apply the changes.

> \# systemctl restart apache2

#### 8\. Run the Setup Wizard

Navigate to your browser and access the setup wizard using your server IP or domain name you have mentioned in vhost conf file.

Once you complete the setup wizar your will redirect to dashbord
