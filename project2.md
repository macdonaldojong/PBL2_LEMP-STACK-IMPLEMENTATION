# WEB STACK IMPLEMENTATION (LEMP STACK)

## Step 1 – Installing the Nginx Web Server

`sudo apt update`

`sudo apt install nginx`

`sudo systemctl status nginx`

First, let us try to check how we can access it locally in our Ubuntu shell, run:

curl http://localhost:80
or
curl http://127.0.0.1:80
 

 ![install nginx](./images/intalling%20nginx.PNG)

 ![nginx running](./images/nginx%20running.PNG)

 
## Step 2 — Installing MySQL
`sudo apt install mysql-server`

`sudo mysql_secure_installation`

`sudo mysql`

`exit`
 
![install mysql](./images/install%20mysql.PNG)


## STEP 3 – INSTALLING PHP

`sudo apt install php-fpm php-mysql`

## Step 4 — Configuring Nginx to Use PHP Processor

`sudo mkdir /var/www/projectLEMP`

`sudo chown -R $USER:$USER /var/www/projectLEMP`

`sudo nano /etc/nginx/sites-available/projectLEMP`

sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
sudo nginx -t

![install nginx ](./images/intalling%20nginx.PNG)


`sudo unlink /etc/nginx/sites-enabled/default`

`sudo systemctl reload nginx`

`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

![install nginx](./images/nginx%20install.PNG)

## Step 5 – Testing PHP with Nginx

`sudo nano /var/www/projectLEMP/info.php`