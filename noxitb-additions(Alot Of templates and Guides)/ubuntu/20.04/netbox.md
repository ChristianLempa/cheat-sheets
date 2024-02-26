## Install NetBox on Ubuntu 22.04

[NetBox](https://github.com/netbox-community/netbox/) is an infrastructure resource modeling (IRM) application designed to empower network automation. NetBox was developed specifically to address the needs of network and infrastructure engineers. It is intended to function as a domain-specific source of truth for network operations.

NetBox runs as a web application atop the Django Python framework with a PostgreSQL database.

#### Prerequisites:

- A Ubuntu 22.04 installed KVM VPS or Dedicated Server.
- A root user access or normal user with administrative privileges

### Install NetBox on Ubuntu 22.04

#### 1\. Keep the server up to date

> \# apt update -y && apt upgrade -y

#### 2\. Install and Configure PostgreSQL Database

We’ll install and configure a local PostgreSQL database.

Note: NetBox requires PostgreSQL 9.6 or higher. Please note that MySQL and other relational databases are not currently supported.

Install PostgreSQL database using following command:

> \# apt install -y postgresql libpq-dev

Next, we need to create a database for NetBox and assign it a username and password for authentication.

> \# sudo -u postgres psql
>
> postgres=# CREATE DATABASE netbox;
>
> CREATE DATABASE
>
> postgres=# CREATE USER netbox WITH PASSWORD ‘r5t6^7$%gyuuyt4’;
>
> CREATE ROLE
>
> postgres=# GRANT ALL PRIVILEGES ON DATABASE netbox TO netbox;
>
> GRANT
>
> postgres=# \\q

#### 3\. Install Redis

Redis is an in-memory key-value store which NetBox employs for caching and queuing. Use following command to install Redis:

> \# apt install redis-server -y

Use the redis-cli utility to ensure the Redis service is functional:

> \# redis-cli ping
>
> PONG

#### 4\. Install and Configure NetBox

There are two ways to install NetBox.

1.  Download a Release Archive
2.  Clone the Git Repository

We’ll install NetBox by cloning the Git repository.

First, install required packages and its dependencies:

> \# apt install -y python3 python3-pip python3-venv python3-dev build-essential libxml2-dev libxslt1-dev libffi-dev libpq-dev libssl-dev zlib1g-dev

Update pip (Python’s package management tool) to its latest release:

> \# pip3 install –upgrade pip

Create the base directory _/opt/netbox_ for the NetBox installation.

> \# mkdir -p /opt/netbox/ && cd /opt/netbox/

Next, clone the master branch of the NetBox GitHub repository into the current directory.

> \# git clone -b master https://github.com/netbox-community/netbox.git .

Create a system user account named netbox. We’ll configure the WSGI and HTTP services to run under this account. We’ll also assign this user ownership of the media directory.

> \# adduser –system –group netbox
>
> \# chown –recursive netbox /opt/netbox/netbox/media/

Move into the NetBox configuration directory and make a copy of *configuration.example.py* named *configuration.py*.

> \# cd /opt/netbox/netbox/netbox/
>
> \# cp configuration_example.py configuration.py

Create a symbolic link of Python binary.

> \# ln -s /usr/bin/python3 /usr/bin/python

Generate a random SECRET_KEY of at least 50 alphanumeric characters.

> \# /opt/netbox/netbox/generate_secret_key.py

Above command will create a secret key, store it so that we can use it in the _configuration.py_.

Open and edit the configuration file *configuration.py*.

> \# nano /opt/netbox/netbox/netbox/configuration.py

The final file should have the following configurations.

> ALLOWED_HOSTS = \[‘\*’\]
>
> DATABASE = {  
> ‘NAME’: ‘netbox’, # Database name you created  
> ‘USER’: ‘netbox’, # PostgreSQL username you created  
> ‘PASSWORD’: ‘r5t6^7$%gyuuyt4’, # PostgreSQL password you set  
> ‘HOST’: ‘localhost’, # Database server  
> ‘PORT’: ”, # Database port (leave blank for default)  
> }
>
> SECRET_KEY = ‘YOUR SECRET KEY’

**Note:**

You can add your domain or server IP in ALLOWED_HOSTS = \[”\] or you can simple enter “\*” for all.

Once NetBox has been configured, we’re ready to proceed with the actual installation.

We’ll run the packaged upgrade script (upgrade.sh) to perform the following actions:

- Create a Python virtual environment
- Install all required Python packages
- Run database schema migrations
- Aggregate static resource files on disk

> \# /opt/netbox/upgrade.sh

Enter the Python virtual environment created by the upgrade script:

> \# source /opt/netbox/venv/bin/activate

Create a superuser account using the createsuperuser

> \# cd /opt/netbox/netbox
>
> \# python3 manage.py createsuperuser

Output:

> Email address: [\[email protected\]](/cdn-cgi/l/email-protection)
>
> Password:
>
> Password (again):
>
> Superuser created successfully.

**Note:**

Remember the username and password. It will require once we finish the installation process to login.

#### 5\. Configure Gunicorn

NetBox ships with a default configuration file for gunicorn. To use it, copy */opt/netbox/contrib/gunicorn.py* to */opt/netbox/gunicorn.py*.

> \# cp /opt/netbox/contrib/gunicorn.py /opt/netbox/gunicorn.py

Copy _contrib/netbox.service_ and _contrib/netbox-rq.service_ to the _/etc/systemd/system/_ directory and reload the systemd dameon:

> \# cp -v /opt/netbox/contrib/\*.service /etc/systemd/system/
> em
> \# systemctl daemon-reload

Start and enable the _netbox_ and _netbox-rq_ services:

> \# systemctl start netbox netbox-rq
>
> \# systemctl enable netbox netbox-rq

#### 6\. Configure Nginx Web Server

Install Nginx web server using following command:

> \# apt install -y nginx

Copy the nginx configuration file provided by NetBox to _/etc/nginx/sites-available/netbox_.

> \# cp /opt/netbox/contrib/nginx.conf /etc/nginx/sites-available/netbox

Edit the netbox configuration file and remove all the content and copy paste below contents:

> \# nano /etc/nginx/sites-available/netbox

Remember to change _server_name_.

> server {  
> listen 80;
>
> \# CHANGE THIS TO YOUR SERVER’S NAME  
> server_name 127.0.0.1;
>
> client_max_body_size 25m;
>
> location /static/ {  
> alias /opt/netbox/netbox/static/;  
> }
>
> location / {  
> proxy_pass http://127.0.0.1:8001;  
> proxy_set_header X-Forwarded-Host $http_host;  
> proxy_set_header X-Real-IP $remote_addr;  
> proxy_set_header X-Forwarded-Proto $scheme;  
> }  
> }

Then, delete */etc/nginx/sites-enabled/default* and create a symlink in the sites-enabled directory to the configuration file you just created.

> \# rm /etc/nginx/sites-enabled/default
>
> \# ln -s /etc/nginx/sites-available/netbox /etc/nginx/sites-enabled/netbox

**Note:**

Above Nginx code will give you error if you use as it is, because it mentioned SSL configuration too. You need to install SSL after the above commands.

Please refer our [How to Install Let’s Encrypt on Nginx Ubuntu](UrlhereUpdate) article to install SSL certificate.

Now test Nginx configuration and restart the Nginx service:

> \# nginx -t
>
> \# systemctl restart nginx

That’s it we have successfully completed with the installation and configuration process.

Navigate to your browser and access NetBox with using either server IP or domain name.
