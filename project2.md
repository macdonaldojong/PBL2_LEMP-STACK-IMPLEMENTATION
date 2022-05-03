# WEB STACK IMPLEMENTATION (LEMP STACK)

## Step 1 – Installing the Nginx Web Server

* sudo apt update
* sudo apt install nginx
* sudo systemctl status nginx

*First, let us try to check how we can access it locally in our Ubuntu shell, run:
==========================
curl http://localhost:80
or
curl http://127.0.0.1:80

![install nginx](./images/intalling%20nginx.PNG)

![nginx running](./images/nginx%20running.PNG)
==========================

## Step 2 — Installing MySQL
* sudo apt install mysql-server
* sudo mysql_secure_installation
* sudo mysql
* exit

![install mysql](./images/install%20mysql.PNG)

## STEP 3 – INSTALLING PHP
* sudo apt install php-fpm php-mysql

## Step 4 — Configuring Nginx to Use PHP Processor

* sudo mkdir /var/www/projectLEMP
* sudo chown -R $USER:$USER /var/www/projectLEMP
* sudo nano /etc/nginx/sites-available/projectLEMP
* sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
* sudo nginx -t
================================
![install nginx ](./images/intalling%20nginx.PNG)
================================
* sudo unlink /etc/nginx/sites-enabled/default
* sudo systemctl reload nginx
* sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s
* http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

![install nginx](./images/nginx%20install.PNG)
================================
## Step5: Testing PHP with Nginx
================================

* sudo nano /var/www/projectLEMP/info.php`
---
<?php
phpinfo();
sudo rm /var/www/your_domain/info.php
---
**For PHP 7: install libapache2-mod-php:

 sudo apt install libapache2-mod-php
================================
![Php running](./images/PHP%20running.PNG)
================================

## STEP6: RETRIEVING DATA FROM MYSQL DATABASE WITH PHP

* sudo mysql
* mysql> CREATE DATABASE `Demo`;
* CREATE USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY 'Password.11';
* mysql> GRANT ALL ON Demo.* TO 'admin'@'%';
* mysql> exit

* mysql -u admin –p
===
CREATE TABLE Demo.todo_list (
    -> item_id INT AUTO_INCREMENT,
    -> content VARCHAR(255),
    -> PRIMARY KEY(item_id));
===
![create mysql table](./images/create%20mysql%20table.PNG)
=============================

* INSERT INTO Demo.todo_list (content) VALUES ("My first important item");
* INSERT INTO Demo.todo_list (content) VALUES ("My second important item");
* INSERT INTO Demo.todo_list (content) VALUES ("My 3rd important item");
* INSERT INTO Demo.todo_list (content) VALUES ("Much more important item are available");
* mysql> exit
* sudo nano /var/www/projectLEMP/todo_list.php

### To display on php, copy this content into your todo_list.php script:
============================
<?php
$user = "admin";
$password = "password.11";
$database = "Demo";
$table = "todo_list";

try {
    $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
    echo "<h2>TODO</h2><ol>";
    foreach($db->query("SELECT content FROM $table") as $row) {
        echo "<li>" . $row['content'] . "</li>";
    }
    echo "</ol>";
    } catch (PDOException $e) {
        print "Error!: " . $e->getMessage() . "<br/>";
        die();
  }
============================
![Todo list](./images/Todo%20list.PNG)




==================== END OF Project=====================

* Remove NGINX from Ubuntu if using previous in project1
* sudo apt remove nginx
* Purge will uninstall NGINX from the system
* sudo apt purge nginx
* Remove Apache web server from Ubuntu
* sudo apt remove apache2

* Remove will uninstall Apache from the system, but leave the configuration files behind
* Purge will uninstall Apache from the system, along with the configuration files inside /etc/apache2
* sudo apt purge apache2
