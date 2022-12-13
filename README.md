# Setup Tools
 

## 1. Install Homebrew 
Install [Homebrew](https://brew.sh/)


## 2. Install Apache2 
Refernce:
<br/>
<br/>
[Javatpoint](https://www.javatpoint.com/how-to-install-apache-on-mac)
<br/>
[digitalocean](https://www.digitalocean.com/community/tutorials/apache-configuration-error-ah00558-could-not-reliably-determine-the-server-s-fully-qualified-domain-name)
       

  	 a. Set  ServerName 127.0.0.1 in location  
/usr/local/etc/httpd/ in httpd.conf change port 8080 to 80

     sudo apachectl start
     sudo apachectl stop

 3.Install Docker  
       https://docs.docker.com/desktop/install/mac-install/

4. Install NPM  and node JS 
      https://nodejs.org/en/download/package-manager/

	brew update 
	brew install node
           
            //Check node version 
            node -v
            npm -v 
5. Install NVM 
       (Node version module)

       https://www.freecodecamp.org/news/node-version-manager-nvm-install-guide/

       curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash


       Export nvm_dir into profile as per attached screenshot.



6.Install PHP
   https://www.php.net/manual/en/install.macosx.packages.php
    
    https://www.geeksforgeeks.org/how-to-install-php-on-macos/

  ~% brew services restart php

7. Install PostgreSql  
Required  install PgAdmin4 GUI  client.
https://www.pgadmin.org/download/pgadmin-4-macos/

Install postgreSQL as db server

https://www.sqlshack.com/setting-up-a-postgresql-database-on-mac/

CREATE ROLE admin WITH LOGIN PASSWORD ‘admin’;
ALTER ROLE admin CREATEDB;












8. Install  Mongodb db server and mongoDB compass.
8.a  install mongoDB compass
      https://www.mongodb.com/try/download/shell

8.b Install mongodb 

             https://github.com/mongodb/homebrew-brew
https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-os-x/


Start mongod as a service

~% brew services start mongodb-community

Start mongoD manually 

~%  mongod --config /usr/local/etc/mongod.conf

9.Docker compose
docker-compose --version
10.Install Postman
 https://www.postman.com/downloads/

11.Install VS code 
https://code.visualstudio.com/docs/setup/mac

12. Install Sublime Text 
https://www.sublimetext.com/3

13. Add VS code extension 

a. Prettier 








14. Run Node js  sample example.
a. Create app.js file and add below line the file.
      		console.log("hello node ");
b. Save app.js file.
c. Run app.js using terminal 

>> node app.js 

d. See the result on the console.


15. PHP sample file executed on apache2 server.

Note: First create folder structure like /Users/ashokdhokare/Sites/test
1. Create a index.php file  and add below code on the file.

<!DOCTYPE html>
<html>
<body>
  <h1>Hello </h1>
  <?php
    echo " Hello Digialpha”;
   ?>
</body>
</html>

2. Save the index.php  file into the below path.

/Users/ashokdhokare/Sites/test
3. Changes on the file  httpd.conf
httpd.conf file  on the path /usr/local/etc/httpd
Change Listen port 8080 to 80
Add   LoadModule php_module /usr/local/opt/php@8.0/lib/httpd/modules/libphp.so
User hartleylab to change your machine      User <Your Machine user>.
ServerName localhost
 Change path  DocumentRoot <"/Users/hartleylab/Sites">  <Directory "/Users/hartleylab/Sites">
Add # Virtual hosts
Include /usr/local/etc/httpd/extra/httpd-vhosts.conf
Attached is a sample file.  
https://drive.google.com/file/d/1O5f8FgbeFXY1S755l15qAnmiGCmr8Wge/view?usp=share_link
4. Changes on file httpd-vhosts.conf 
httpd-vhosts.conf  file on  path  http/usr/local/etc/httpd/extra 
Add new virtual host 
<VirtualHost *:80>
    ServerAdmin webmaster@dummy-host2.example.com
    DocumentRoot "/Users/ashokdhokare/Sites/test"
    ServerName test.local
    ErrorLog "/usr/local/var/log/httpd/demo-error_log"
    CustomLog "/usr/local/var/log/httpd/demo-access_log" common
</VirtualHost>

Attached is sample file

https://drive.google.com/file/d/1iweg2gR815JoqhTPeSWdm8j3WiLrBf5w/view?usp=share_link

	5. Run the code on the browser using your ServerName.

		

Note: Highlight mark line should be changed.


 16. Install  Redis 
https://redis.io/docs/getting-started/installation/install-redis-on-mac-os/




