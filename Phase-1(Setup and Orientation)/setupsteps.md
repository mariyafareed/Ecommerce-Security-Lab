🔹 Objective
Set up a simulated e-commerce environment using OpenCart on a Ubuntu Virtual Machine with Apache, MySQL, and PHP.

✅ Steps
🖥️ Step 1: Set Up Ubuntu VM in VirtualBox
Download Ubuntu 22.04 LTS ISO from ubuntu.com.

*In VirtualBox, create a new VM:*

Name: Ecommerce-Ubuntu

Type: Linux, Version: Ubuntu (64-bit)

RAM: 4096 MB

Disk: 30 GB (dynamically allocated)

Attach the ISO and install Ubuntu normally.

After installation, run:
"sudo apt update && sudo apt upgrade -y"


🌐 Step 2: Install LAMP Stack (Apache, MySQL, PHP):
"sudo apt install apache2 mysql-server php php-mysql libapache2-mod-php unzip curl -y"

Install required PHP extensions:

"sudo apt install php-zip php-curl php-gd php-mbstring php-intl php-bcmath -y"

Restart Apache:

"sudo systemctl restart apache2"


🧰 Step 3: Download and Set Up OpenCart

Download latest OpenCart ZIP:

"cd /var/www/html

sudo wget https://github.com/opencart/opencart/releases/download/4.0.2.3/opencart-4.0.2.3.zip

sudo unzip opencart-4.0.2.3.zip

sudo mv upload/* .

sudo mv upload/.* . 2>/dev/null

sudo rm -r upload opencart-4.0.2.3.zip"

Rename configuration files:

sudo mv config-dist.php config.php

sudo mv admin/config-dist.php admin/config.php

Set permissions:

"sudo chown -R www-data:www-data /var/www/html"

🛢️ Step 4: Configure MySQL Database

"sudo mysql -u root -p"

Inside the MySQL shell:

sql

CREATE DATABASE opencart;

CREATE USER 'ocuser'@'localhost' IDENTIFIED BY 'StrongPass@123';

GRANT ALL PRIVILEGES ON opencart.* TO 'ocuser'@'localhost';

FLUSH PRIVILEGES;

EXIT;

🌐 Step 5: Install OpenCart via Web Browser

Find your VM's IP:

ip a

Visit in browser: http://<your-ip>

Complete the installer:

DB Host: localhost

DB User: ocuser

DB Password: StrongPass@123

DB Name: opencart

Choose admin username and password

After successful install, remove the install folder:
sudo rm -rf  /var/www/html/install
