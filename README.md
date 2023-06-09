
<p align="center">
 <img width="100px" src="https://avatars.githubusercontent.com/u/48676778?v=4" align="center" alt="GitHub Readme Stats" />
 <h2 align="center">Magento Helping Guide</h2>
 <p align="center">Get dynamically generated GitHub stats on your READMEs!</p>
</p>
  <p align="center">
    <a href="https://github.com/anuraghazra/github-readme-stats/actions">
      <img alt="Tests Passing" src="https://github.com/anuraghazra/github-readme-stats/workflows/Test/badge.svg" />
    </a>
    <a href="https://github.com/anuraghazra/github-readme-stats/graphs/contributors">
      <img alt="GitHub Contributors" src="https://img.shields.io/github/contributors/anuraghazra/github-readme-stats" />
    </a>
    <a href="https://codecov.io/gh/anuraghazra/github-readme-stats">
      <img src="https://codecov.io/gh/anuraghazra/github-readme-stats/branch/master/graph/badge.svg" />
    </a>
    <a href="https://github.com/anuraghazra/github-readme-stats/issues">
      <img alt="Issues" src="https://img.shields.io/github/issues/anuraghazra/github-readme-stats?color=0088ff" />
    </a>
    <a href="https://github.com/anuraghazra/github-readme-stats/pulls">
      <img alt="GitHub pull requests" src="https://img.shields.io/github/issues-pr/anuraghazra/github-readme-stats?color=0088ff" />
    </a>
    <br />
    <br />
    <a href="https://a.paddle.com/v2/click/16413/119403?link=1227">
      <img src="https://img.shields.io/badge/Supported%20by-VSCode%20Power%20User%20%E2%86%92-gray.svg?colorA=655BE1&colorB=4F44D6&style=for-the-badge"/>
    </a>
    <a href="https://a.paddle.com/v2/click/16413/119403?link=2345">
      <img src="https://img.shields.io/badge/Supported%20by-Node%20Cli.com%20%E2%86%92-gray.svg?colorA=61c265&colorB=4CAF50&style=for-the-badge"/>
    </a>
  </p>

#### Commands to setup PHP and Nginx in Ubuntu
###### <small>Let’s quickly review this PHP and Nginx tutorial. These are all of the commands that we used to enable the fastCGI process manager for PHP in Nginx:</small>
* `sudo apt-get update -y`
* `sudo apt-get upgrade -y`
* `sudo apt-get install nginx -y`
* `sudo systemctl status nginx`
* `sudo apt-get install php8.1-fpm -y`
* `sudo systemctl status php8.1-fpm`
* `sudo nano /etc/nginx/sites-available/default`
* `sudo nginx -t`
* `sudo systemctl restart nginx`
* `sudo chmod -R 777 /var/www/html`
* `echo "<?php phpinfo(); ?>" >> /var/www/html/info.php`

#####	XdeBug Settings
* `sudo nano /etc/php/8.1/cli/conf.d/20-xdebug.ini`
    ```
    xdebug.remote_enable = 1
    xdebug.remote_port = 9898
    xdebug.idekey = “PHPSTORM”
    xdebug.show_error_trace = 1
    xdebug.remote_autostart = 0
    xdebug.mode=debug
    xdebug.client_port=9898
    ```
* in project file `sudo chown $USER:$USER -R .`

> #####	Remove Apache2 & install nginx + mariadb-server&client
* `apt-get upgrade`
***
* `apt-get purge apache2`
* `systemctl disable apache2`
* `sudo apt-get remove apache2`
***
* `apt install -y nginx`
* `systemctl enable nginx`
* `systemctl start nginx`
***
* `apt-add-repository ppa:ondrej/php -y`
* `systemctl enable php7.4-fpm`
* `systemclt start php7.4-fpm`
* `apt install -y php7.4 php7.4-{cli,gd,curl,mysql,ldap,zip,fileinfo,fpm,xml,mbstring,exif,pspell,imagick,bcmath}`
***
* `apt install mariadb-server-10.6 mariadb-client-10.6`
* `systemctl enable mariadb`
* `systemctl start mariadb`
* `mysql_secure_installation`
* `wget -O composer-setup.php https://getcomposer.org/installer`
* `php composer-setup.php --install-dir=/usr/bin --filename=composer`
* `cd /var/www/html`
* `composer create-project laravel/laravel .`
* `chown www-data:www-data /var/www/html -R`
* `mysql -e "CREATE USER 'laravel'@'localhost' IDENTIFIED BY '<PASSWORD-HERE>';"`
* `mysql -e "CREATE DATABASE laravel;"`
* `mysql -e "GRANT ALL PRIVILEGES ON laravel.* to 'laravel'@'localhost';"`
* `ls /var/run/php/php8.1-fpm.sock`
* `nano /etc/nginx/sites-available/`
* `cd /var/www/eg_umair/html/`
* `cd ..`
* `ls -al`
* `chown www-data:www-data html -R`


> **Note** if system hangs much often then do this
* go to etc folder
  * `/etc/elasticsearch/`
  * `open "jvm.options" file then`
* find JVM heap size
  * in there replace ## `-Xms4G` && `-Xmx4G ` to  `-Xms100m` `-Xmx4G` with nextline tab seprated.
  * `then restart elasticsearch`
  * `sudo service elasticsearch restart`


>#### _**Give permission**_
* `cd /var/www/html/magento`
* `ll`
* `sudo chmod -R 777 var/ pub/ generated/ app/etc/` ( if server url is not working and loading site then run this command )
* test by --- http://magento.local.com
* if error  or for refresh file
  - `sudo chmod -R 777 var/ pub/ generated/ app/etc/`  in `/var/www/html/magento` folder or `select your magento folder` pointed
  - `sudo rm -rf /etc/nginx/sites-enabled/magento.local.com`
  - `sudo ln -s /etc/nginx/sites-available/magento.local.com /etc/nginx/sites-enabled/`
  - `sudo service nginx restart`
  - `sudo systemctl restart nginx.service`


> ##### sudo apt-get update
* Check Version of required setup before Installation
  - Composer: 
    - `composer` or `composer --version`
  - PHP: 
    - `php -v`
  - MySQL: 
    - `mysql -V` OR `mysql -v`
  - Elasticsearch: 
    - `curl -XGET 'http://localhost:9200'`
  - For Swap on or off
    - `swapon -p 0 /dev/sdc1`
    - `swapoff -a`
    - `swapon -a`
		
> ##### sudo apt update
* sudo apt update


> ##### sudo install composer
* `sudo apt update`  `sudo apt install php-cli unzip` go to root `cd ~`
  * `curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php`
  * `HASH='curl -sS https://composer.github.io/installer.sig'`
  * `php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } 
     else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`
  * `sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer`


##	4): sudo install php 7.*, 8.*
		-- systemctl status php8.1-fpm
		-- systemctl restart php8.1-fpm
		-- sudo apt update
		-- sudo apt install --no-install-recommends php8.1
		-- sudo apt-get install php8.1-PACKAGE_NAME --> { sudo apt-get install php8.1-PACKAGE_NAME }
		-- sudo apt install php8.1-{gd,zip,mysql,oauth,yaml,fpm,mbstring,memcache,dom,xml,bcmath,ctype,curl,iconv,intl,soap,xsl,sockets}
		-- change php version 
			- https://hostadvice.com/how-to/how-to-switch-between-php-versions-on-an-ubuntu-22-04-vps-or-dedicated-server/#:~:text=By%20default%2C%20Ubuntu%20will%20set%20the%20latest%2C%20stable,%24%20sudo%20a2dismod%20php8.1%20%24%20sudo%20a2enmod%20php7.2	
			- sudo apt upgrade
			- sudo apt install software-properties-common apt-transport-https
			- sudo add-apt-repository ppa:ondrej/php
			- sudo apt update
			- sudo apt install php8.1 libapache2-mod-php8.1
			- sudo a2dismod php8.1
			- sudo a2enmod php7.2
			- sudo service apache2 restart
			- sudo update-alternatives --config php
		
##	5): sudo install mysql 5.6, 5.7
		-- remove all mysql dir 
			- sudo apt-get remove --purge mysql*
			- sudo apt-get autoremove
			- sudo apt-get autoclean
					** OR **
			- https://www.linuxshelltips.com/completely-uninstall-mysql-server-in-ubuntu/
		-- sudo systemctl disable mysql.service
		-- sudo systemctl enable mysql.service
		-- sudo systemctl restart mysql.service
		-- sudo systemctl start mysql.service
		
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
			- sudo rm -rf /etc/elasticsearch
			
##	8): Install Magento 2
		--0 /home/eg-umair/.config/composer/auth.json  accessKey stored address
		--1 sudo apt update
		--2 Get Magento marketplace accesskey  
			- https://marketplace.magento.com/customer/accessKeys/  --->  Public Key: de686a15f9d741f7739c92c5eefa190d   Private Key: f505c128e18d79b04e2921c253459942
		--3 cd /var/www/html
		--4 composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
			- composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition magento
			- composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition magento
			- composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.3.2-p1 luma
		--5 Set file permissions:
			- sudo chown -R $USER:$USER /var/www/html
			- sudo chown -R :www-data /var/www/html/
			- sudo chmod -R 755 /var/www/html/magento/
			
			
		--6 Setup MySQL Database
			- sudo apt update
			- sudo mysql -u root -p
				~ CREATE DATABASE magento2db;
				~ CREATE USER 'laravel'@'localhost' IDENTIFIED BY '<PASSWORD-HERE>';
				~ CREATE DATABASE laravel;
				~ GRANT ALL PRIVILEGES ON laravel.* to 'laravel'@'localhost';
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
				~ sudo chmod -R 777 var/ pub/ generated/ app/etc/  --->                  ( if server url is not working and loading site then run this command )
				~ test by ---> http://magento.local.com
				~ #if error  or for refresh file
					--- sudo chmod -R 777 var/ pub/ generated/ app/etc/  --> in '/var/www/html/magento' folder or select your magento folder pointed
					--- sudo rm -rf /etc/nginx/sites-enabled/magento.local.com
					--- sudo ln -s /etc/nginx/sites-available/magento.local.com /etc/nginx/sites-enabled/
					--- sudo service nginx restart
					--- sudo systemctl restart nginx.service
				
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
			- sudo chmod -R 777 var/ pub/ generated/ app/etc/
			
		--9 Frontend URL:
			- http://magento2.local/
			- Backend URL:
			- http://magento2.local/admin
			- User: admin
			- Password: admin@123
		--10 Disable Two-Factor Authorization:
			- sudo php bin/magento module:disable Magento_TwoFactorAuth
			- sudo php bin/magento cache:flush
		       		**__OR__**
			- Open app/etc/config.php and change value for 'Magento_TwoFactorAuth' to 0.
			- Now execute php bin/magento setup:di:compile
							       
			- php bin/magento sampledata:deploy
		        - php bin/magento setup:upgrade
			- php bin/magento setup:di:compile
			- php bin/magento setup:static-content:deploy -f
		--11 Switch to production mode:
			- sudo php bin/magento deploy:mode:set production
			- sudo php bin/magento cache:flush
		--12 Switch to developer mode:
			- sudo php bin/magento deploy:mode:set developer
			- sudo php bin/magento cache:flush

##	***): sudo: /etc/sudoers is owned by uid 1000, should be 0
		-- pkexec chown root:root /etc/sudoers /etc/sudoers.d -R
					OR 
		-- sudo chown myuser:myuser /etc/sudoers 
		-- chmod u+w /etc/sudoers
		-- chmod u-w /etc/sudoers
		-- sudo chown root:root /etc/sudoers 


##	*0): Use self-assign Open ssl 
		-- sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt
		-- While using OpenSSL, you should also create a strong Diffie-Hellman (DH) group
			- sudo openssl dhparam -out /etc/nginx/dhparam.pem 4096
		-- sudo nano /etc/nginx/snippets/self-signed.conf
		-- you’ve added those lines, save the file and exit the editor. If you used nano to edit the file, you can do so by pressing CTRL + X, Y, then ENTER
			- ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
			- ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;
		-- sudo nano /etc/nginx/snippets/ssl-params.conf
		-- Add the following into your **ssl-params.conf** snippet file:
			```
				ssl_protocols TLSv1.3;
				ssl_prefer_server_ciphers on;
				ssl_dhparam /etc/nginx/dhparam.pem; 
				ssl_ciphers EECDH+AESGCM:EDH+AESGCM;
				ssl_ecdh_curve secp384r1;
				ssl_session_timeout  10m;
				ssl_session_cache shared:SSL:10m;
				ssl_session_tickets off;
				ssl_stapling on;
				ssl_stapling_verify on;
				resolver 8.8.8.8 8.8.4.4 valid=300s;
				resolver_timeout 5s;
				# Disable strict transport security for now. You can uncomment the following
				# line if you understand the implications.
				#add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload";
				add_header X-Frame-Options DENY;
				add_header X-Content-Type-Options nosniff;
				add_header X-XSS-Protection "1; mode=block";
			```
		-- sudo cp /etc/nginx/sites-available/**your_domain** /etc/nginx/sites-available/**your_domain**.bak
		-- sudo nano /etc/nginx/sites-available/**your_domain**
		-- **Note:** Use a 302 redirect until you have verified that everything is working properly. After, you will change this to a permanent 301 redirect.
			- add these in file 
				```
					server {
					    listen 443 ssl;
					    listen [::]:443 ssl;
					    include snippets/self-signed.conf;
					    include snippets/ssl-params.conf;
					root /var/www/**your_domain**/html;
						index index.html index.php index.htm index.nginx-debian.html;
					  server_name your_domain.com www.your_domain.com;
					  location / {
							try_files $uri $uri/ =404;
						}
					}
				```
			- alse add after **}** this
				```
					server {
					    listen 80;
					    listen [::]:80;

					    server_name your_domain.com www.your_domain.com;

					    return 302 https://$server_name$request_uri;
					}
				```
		-- sudo ufw app list
		-- sudo ufw status
			- sudo ufw allow 'Nginx Full'
			- sudo ufw delete allow 'Nginx HTTP'
		-- sudo ufw status
		-- sudo nginx -t
		-- sudo systemctl restart nginx
		-- sudo nano /etc/nginx/sites-available/**your_domain**
			- sudo nano /etc/nginx/sites-available/your_domain
				~ sudo nano /etc/nginx/sites-available/**your_domain**
		-- sudo nginx -t
		-- sudo systemctl restart nginx
		

##	 0): Use Certbot to Enable HTTPS with NGINX on Ubuntu
    -- self assign openssl
        - https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-20-04-1
    -- sudo apt install certbot python3-certbot-nginx
        - sudo nginx -t
        - sudo systemctl reload nginx
        - sudo ufw status
        - sudo certbot --nginx -d example.com -d www.example.com
        
        
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
    

> ##### Install B2B with Composer
- composer require magento/extension-b2b
- enter your [authentication keys](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html?_ga=2.189836459.1829582113.1686125249-664196562.1686125249) ---> you have stored your public and private keys in auth.json
- sudo bin/magento setup:upgrade
- sudo bin/magento setup:di:compile
- sudo bin/magento setup:static-content:deploy -f
- sudo bin/magento cache:clean
- sudo bin/magento indexer:reindex
- sudo chmod -R 777 var/ pub/ generated/ app/etc/

> ##### Install B2B:Consumers with Composer [Consumers list](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/start-message-queues.html?lang=en)
- sudo bin/magento queue:consumers:list
  * product_action_attribute.update
  * product_action_attribute.website.update
  * exportProcessor
  * codegeneratorProcessor
  * sales.rule.update.coupon.usage
  * sales.rule.quote.trigger.recollect
  * media.storage.catalog.image.resize
  * matchCustomerSegmentProcessor
  * staging.synchronize_entity_period
  * product_alert
  * negotiableQuotePriceUpdate
  * sharedCatalogUpdatePrice
  * sharedCatalogUpdateCategoryPermissions
  * inventory.source.items.cleanup
  * inventory.mass.update
  * inventory.reservations.cleanup
  * inventory.reservations.update
  * inventory.reservations.updateSalabilityStatus
  * inventory.indexer.sourceItem
  * inventory.indexer.stock
  * media.content.synchronization
  * media.gallery.renditions.update
  * media.gallery.synchronization
  * placeOrderProcessor
  * purchaseorder.toorder
  * purchaseorder.transactional.email
  * purchaseorder.validation
  * quoteItemCleaner
  * inventoryQtyCounter
  * commerce.eventing.event.publish
  * async.operations.all

- sudo bin/magento queue:consumers:start sharedCatalogUpdatePrice
- sudo bin/magento queue:consumers:start sharedCatalogUpdateCategoryPermissions
- ###### **In Case of Errors** Add these in your cron tabs
  - `* * * * * ps ax | grep [s]haredCatalogUpdateCategoryPermissions >>/dev/null 2>&1 || nohup php /var/www/html/magento2/bin/magento queue:consumers:start sharedCatalogUpdateCategoryPermissions &`
  - `* * * * * ps ax | grep [s]haredCatalogUpdatePrice >>/dev/null 2>&1 || nohup php /var/www/html/magento2/bin/magento queue:consumers:start sharedCatalogUpdatePrice &`

	
> ##### Create Magento Modeule
- Unit1/HelloWorld/etc/module.xml
	```
	<?xml version="1.0"?>
	<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
	    <module name="Unit1_HelloWorld">

	    </module>
	</config>
	```
- Unit1/HelloWorld/registration.php
	```
	<?php
	use Magento\Framework\Component\ComponentRegistrar;
	ComponentRegistrar::register(
	    ComponentRegistrar::MODULE,
	    'Unit1_HelloWorld',
	    __DIR__
	);
	```
- php bin/magento module:enable Unit1_HelloWorld
- php bin/magento setup:upgrade
- sudo chmod -R 777 var/ pub/ generated/ app/etc/
	
> ##### Initial Server Setup with Ubuntu 20.04
* Step 1 — `sudo apt update`
  * `curl -4 icanhazip.com`  --> { your_server_ip }
  * `ssh root@your_server_ip`
* Step 2 — Creating a New User
    - add user 
      - `adduser testuser`
* Step 3 — Granting Administrative Privileges
    - `usermod -aG sudo testuser`
			
			
