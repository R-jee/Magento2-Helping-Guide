>#	Magento Helping Guide

##	1): sudo apt-get update
		-- Check Version of required setup before Installation
			- Composer: composer or composer --version
			- PHP: php -v
			- MySQL: mysql -V OR mysql -v
			- Elasticsearch: curl -XGET 'http://localhost:9200'
			- swapon -p 0 /dev/sdc1
			- swapoff -a
			- swapon -a
			
##	2): sudo apt update
##	3): sudo install composer
		-- sudo apt update
		-- sudo apt install php-cli unzip
		-- cd ~
		-- curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
		-- HASH=`curl -sS https://composer.github.io/installer.sig`
		-- php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } 
		   else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
		-- sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer

##	4): sudo install php 7.*, 8.*
		-- sudo apt update
		-- sudo apt install --no-install-recommends php8.1
		-- sudo apt-get install php8.1-PACKAGE_NAME --> { sudo apt-get install php8.1-PACKAGE_NAME }
		-- sudo apt install php8.1-{gd,zip,mysql,oauth,yaml,fpm,mbstring,memcache,dom,xml,bcmath,ctype,curl,iconv,intl,soap,xsl,sockets}
		-- change php version 
			- https://hostadvice.com/how-to/how-to-switch-between-php-versions-on-an-ubuntu-22-04-vps-or-dedicated-server/#:~:text=By%20default%2C%20Ubuntu%20will%20set%20the%20latest%2C%20stable,%24%20sudo%20a2dismod%20php8.1%20%24%20sudo%20a2enmod%20php7.2	
		
		
##	5): sudo install mysql 5.6, 5.7
		-- sudo apt update
		-- sudo apt install mysql-server   
		-- sudo systemctl start mysql.service
				OR
		-- sudo mysql_secure_installation 
			- sudo mysql
			- ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'admin';  
				ALTER USER command to change the 'root' user’s authentication method to one that uses a 'password'. 
			- exit
			- pass -> admin@123 : name -> root
		-- mysql -u root -p  --> { access mysql scure with pass }
		-- Creating a Dedicated MySQL User and Granting Privileges
			- sudo mysql
			- mysql -u root -p
			- CREATE USER 'admin'@'host' IDENTIFIED WITH authentication_plugin BY 'admin@123'; -->  { MySQL’s default plugin, caching_sha2_password. }
			- CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';

##	6): Install Nginx
		-- sudo apt update
		-- sudo apt install nginx
		-- Step 2 – Adjusting the Firewall
			- This list displays three profiles available for Nginx:
				~ Nginx Full: This profile opens both port 80 (normal, unencrypted web traffic) and port 443 (TLS/SSL encrypted traffic)
				~ Nginx HTTP: This profile opens only port 80 (normal, unencrypted web traffic)
				~ Nginx HTTPS: This profile opens only port 443 (TLS/SSL encrypted traffic)
			- sudo ufw app list
			- sudo ufw allow 'Nginx Full'
			- sudo ufw status
			- systemctl status nginx
		-- Step 3 – Checking your Web Server
			- systemctl status nginx
			- ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
					OR
			- curl -4 icanhazip.com
		-- Step 4 – Managing the Nginx Process
			- web server
				stop  	-->	sudo systemctl stop nginx
				start 	--> 	sudo systemctl start nginx
				restart -->	sudo systemctl restart nginx
				reload  -->	sudo systemctl reload nginx 
				disable -->	sudo systemctl disable nginx
				startup -->	sudo systemctl enable nginx
		-- Step 5 – Setting Up Server Blocks (Recommended)
			- Create the directory for your_domain as follows, using the -p flag to create any necessary parent directories:
				~ sudo mkdir -p /var/www/your_domain/html
			- Assign ownership of the directory with the $USER environment variable:
				~ sudo chown -R $USER:$USER /var/www/your_domain/html
			- permissions of your web roots should be correct if you haven’t modified your umask value (Recommended)
				~ sudo chmod -R 755 /var/www/your_domain
			- create a sample index.html page using nano or your favorite editor
				~ nano /var/www/your_domain/html/index.html
			- In order for Nginx to serve this content, it’s necessary to create a server block with the correct directives.
				~ sudo nano /etc/nginx/sites-available/your_domain
				~ server {
					listen 80;
					listen [::]:80;

					root /var/www/your_domain/html;
					index index.html index.htm index.nginx-debian.html;

					server_name your_domain.com www.your_domain;

					location / {
						try_files $uri $uri/ =404;
					}
				 }
			- Next, enable the file by creating a link from it to the sites-enabled directory, which Nginx reads from during startup
				~ sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
			- It is necessary to adjust a single value in the /etc/nginx/nginx.conf file. Open the file
				~ sudo nano /etc/nginx/nginx.conf
				~ Find the 'server_names_hash_bucket_size' directive and remove the # symbol to uncomment the line:
			- test to make sure that there are no syntax errors in any of your Nginx files
				~ sudo nginx -t
			- sudo systemctl restart nginx
				
##	7): Install ElasticSearch
		-- sudo apt update
		-- curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
		-- echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
		-- sudo apt update
		-- sudo apt install elasticsearch
		-- Step 2 — Configuring Elasticsearch
			- sudo nano /etc/elasticsearch/elasticsearch.yml
				~ network.host: localhost 
			- elasticsearch 
				stop  	-->	sudo systemctl stop elasticsearch
				start 	--> 	sudo systemctl start elasticsearch
				restart -->	
				reload  -->	
				disable -->	sudo systemctl disable elasticsearch
				startup -->	sudo systemctl enable elasticsearch
		-- Step 3 — Securing Elasticsearch
			- 
		-- Step 4 Error in ElasticSearch Solved by
			- sudo apt-get --purge autoremove elasticsearch
			
##	8): Install Magento 2
		--1 sudo apt update
		--2 Get Magento marketplace accesskey  
			- https://marketplace.magento.com/customer/accessKeys/
		--3 cd /var/www/html
		--4 composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
			- composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition magento
		--5 Set file permissions:
			- sudo chown -R $USER:$USER /var/www/html
			- sudo chown -R :www-data /var/www/html/
			- sudo chmod -R 755 /var/www/html/magento/
			
			
		--6 Setup MySQL Database
			- sudo apt update
			- sudo mysql -u root -p
				~ CREATE DATABASE magento2db;
				~ CREATE USER 'magento2user'@'localhost' IDENTIFIED BY 'admin@123';
				~ GRANT ALL ON magento2db.* TO 'root'@'localhost' IDENTIFIED BY 'admin@123' WITH GRANT OPTION;
				~ FLUSH PRIVILEGES;
				~ exit;
				
		--7 Setup Virtual Hosts	
				***  START FOR Nginx  ***
			- cd /etc/nginx/sites-enabled/
			- cd /etc/nginx/sites-available/
			- sudo systemctl status nginx status
			- sudo nano /etc/nginx/sites-available/magento.local.com
				upstream fastcgi_backend {
					server unix:/run/php/php8.1-fpm.sock;
				}
				server {
					listen 80;
					server_name magento.local.com;
					set $MAGE_ROOT /var/www/html/magento;
					set $MAGE_MODE developer;
					#set $MAGE_RUN_TYPE store;
					include /var/www/html/magento/nginx.conf.sample;
				}
			- sudo ln -s /etc/nginx/sites-available/magento.local.com /etc/nginx/sites-enabled/		

			- sudo nano etc/hosts
				~ add  ( 172.0.0.1	magento.local.com )  -> save
				~ sudo nginx -t
				~ sudo systemctl restart nginx.service
			- Give permission :: 
				~ cd /var/www/html/magento
				~ ll
				~ sudo chmod -R 777 var/ pub/ generated/ app/etc/  --->   ( if server url is not working and loading site then run this command )
				~ test by ---> http://magento.local.com
				~ if error  or for refresh file
					--- sudo rm -rf /etc/nginx/sites-enabled/magento.local.com
					--- sudo ln -s /etc/nginx/sites-available/magento.local.com /etc/nginx/sites-enabled/
					--- sudo service nginx restart
				
			- sudo nano /etc/nginx/nginx.conf
			- sudo nano /var/www/html/magento.local/nginx.conf.sample;
			- sudo systemctl restart nginx.service
			- sudo nano magento.local.com
			- sudo nginx -t
			- 	
			
				***  END FOR Nginx  ***
				
				***  START FOR Apache2  *** ---> ( IS not verified )
			- sudo nano /etc/apache2/sites-available/magento2.conf
			- <VirtualHost *:80>
				ServerAdmin admin@domain.com
				ServerName magento2.local
				ServerAlias magento2.local
				DocumentRoot /var/www/html/magento2/pub
				<Directory /var/www/html/magento2/>
				Options Indexes FollowSymLinks MultiViews
				AllowOverride All
				Order allow,deny
				allow from all
				</Directory>
				ErrorLog ${APACHE_LOG_DIR}/magento_error.log
				CustomLog ${APACHE_LOG_DIR}/magento_access.log combined
			  </VirtualHost>
			- sudo nano /etc/hosts
			- 127.0.0.1   magento2.local
			- sudo a2ensite magento2.conf
			- sudo a2enmod rewrite
			- sudo service apache2 restart
				***  END FOR Apache2  *** <--- ( IS not verified )
		--8 Install Magento2
			- cd /var/www/html/magento/
			sudo php bin/magento setup:install --base-url=http://magento.local.com --db-host=localhost --db-name=magento --db-user=magento2user --db-password=admin@123 --admin-firstname=Magento --admin-lastname=User --admin-email=admin@mystore.com --admin-user=admin --admin-password=admin@123 --language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 --backend-frontname="admin" --search-engine=elasticsearch7 --elasticsearch-host=localhost --elasticsearch-port=9200
			
			- sudo chmod -R 755 /var/www/html/magento
			- sudo php bin/magento setup:upgrade
			- sudo php bin/magento setup:di:compile
			- sudo php bin/magento setup:static-content:deploy -f
			- sudo php bin/magento indexer:reindex
			- sudo php bin/magento cache:clean
			- sudo php bin/magento cache:flush
			- sudo chmod -R 777 pub/ var/ generated/
			
		--9 Frontend URL:
			- http://magento2.local/
			- Backend URL:
			- http://magento2.local/admin
			- User: admin
			- Password: admin@123
		--10 Disable Two-Factor Authorization:
			- sudo php bin/magento module:disable Magento_TwoFactorAuth
			- sudo php bin/magento cache:flush
		--11 Switch to production mode:
			- sudo php bin/magento deploy:mode:set production
			- sudo php bin/magento cache:flush
		--12 Switch to developer mode:
			- sudo php bin/magento deploy:mode:set developer
			- sudo php bin/magento cache:flush

##	***): sudo: /etc/sudoers is owned by uid 1000, should be 0
		-- pkexec chown root:root /etc/sudoers /etc/sudoers.d -R

##	 0): Use Certbot to Enable HTTPS with NGINX on Ubuntu
		-- Configuring Firewall Rules with UFW
			- If UFW is not installed, install it now using apt or apt-get
				~ sudo apt update
				~ sudo apt install ufw
			- Add firewall rules to allow ssh (port 22) connections as well as http (port 80) and https (port 443) traffic.
				~ sudo ufw allow ssh
				~ sudo ufw allow http
				~ sudo ufw allow https
			- Enable UFW if its not already enabled.
				~ sudo ufw enable
				~ sudo ufw status
		-- Installing Snapd
			- Installing Snapd
				~ sudo apt update
				~ sudo apt install snapd
			- Install the core snap.
				~ sudo snap install core
				~ sudo snap refresh core
		-- Installing Certbot
			- Remove any previously installed certbot packages to avoid conflicts with the new Snap package.
				~ sudo apt remove certbot
			- sudo apt remove certbot
				~ sudo snap install --classic certbot
			- Configure a symbolic link to the Certbot directory using the ln command.
				~ sudo ln -s /snap/bin/certbot /usr/bin/certbot
		-- Requesting a TLS/SSL Certificate Using Certbot
			- Request a certfifcate and automatically configure it on NGINX (recommended):
				~ sudo certbot --nginx
		-- Renewing a TLS/SSL Certificate Using Certbot
			- Test Automated Renewals
				~ sudo certbot renew --dry-run
				~ Manually Renew Certificate
			- Manually Renew Certificate
				~ Manually Renew Certificate
		

##	00): Initial Server Setup with Ubuntu 20.04
		-- sudo apt update
		-- curl -4 icanhazip.com  --> { your_server_ip }
		-- ssh root@your_server_ip
		-- Step 2 — Creating a New User
			- add user --> { adduser testuser }
		-- Step 3 — Granting Administrative Privileges
			- usermod -aG sudo testuser
			
			
