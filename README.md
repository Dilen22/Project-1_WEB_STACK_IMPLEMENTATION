# Project-1

**Web-Stack-Implementation**


![Screenshot 2024-07-07 132314](https://github.com/user-attachments/assets/8a3e02f2-ec27-4648-8a98-62cac578d976)


## Introduction

This project offers a collection of scripts designed to deploy a LAMP stack website within the AWS Cloud environment.

## Features

- **INSTALLING APACHE AND UPDATING THE FIREWALL:** Apache HTTP server can respond to requests from the Internet.
- **INSTALLING MYSQL:** to be able to store and manage data for your site in a relational database.
- **CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE:** To check Dependencies.
- **ENABLE PHP ON THE WEBSITE:** relevant information about your PHP server through that page.

## Installation and Setup

1. **INSTALLING APACHE AND UPDATING THE FIREWALL**

Install Apache using Ubuntu’s package manager ‘apt’:

 ```
sudo apt update
sudo apt install apache2
sudo systemctl status apache2
curl http://localhost:80
or
 curl http://127.0.0.1:80
#Test Apache HTTP server Request from Internet
http://<Public-IP-Address>:80
#Retrive Public IP address, other than AWS console
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
 ```

![Screenshot 2024-07-07 102450](https://github.com/user-attachments/assets/1de30259-a249-4cc5-b601-5207f4135363)
![Screenshot 2024-07-07 102344](https://github.com/user-attachments/assets/7a2a5784-7b87-47a7-bad0-643c1504f024)


2. **INSTALLING MYSQL**

 ```
sudo apt install mysql-server
sudo MySQL
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
sudo mysql_secure_installation
sudo apt install php libapache2-mod-php php-mysql
php -v
 ```

![Screenshot 2024-07-07 112115](https://github.com/user-attachments/assets/bb869a2c-4cd9-4c04-af54-75dabd52cddf)



3. ** CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE**

```
sudo mkdir /var/www/projectlamp
sudo chown -R $USER:$USER /var/www/projectlamp
sudo vi /etc/apache2/sites-available/projectlamp.conf
sudo a2ensite projectlamp
#cREATE INDEX.HTML FILE FOR VIRTUAL HOST
sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' 
$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
http://<Public-IP-Address>:80
```

4. **ENABLE PHP ON THE WEBSITE**

```
sudo vim /etc/apache2/mods-enabled/dir.conf
```
Create a new file named index.php inside your custom web root folder:

```
vim /var/www/projectlamp/index.php
```

This will open a blank file. Add the following text, which is valid PHP code, inside the file:

```
<?php
phpinfo();
```
![Screenshot 2024-07-07 132314](https://github.com/user-attachments/assets/a0c82d2b-048b-4b06-a2da-8e6d2316632c)

