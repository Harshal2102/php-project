# 🚀 PHP Signup Form Deployment on AWS EC2 (Nginx + PHP + MariaDB)




# 📖 Introduction
This project is a simple PHP signup form web application deployed on an AWS EC2 instance. The user fills in a form (name, email, website, comment, gender). The data is processed by a PHP script and stored in a MariaDB database. A success page then shows the submitted information. The goal of this project is to practice deploying a complete LAMP-style stack (with Nginx instead of Apache) on the AWS cloud, from launching the server to verifying the data in the database.



# 🛠️ Technologies Used
AWS EC2 (t3.micro):-Cloud server to host the application

Nginx:-Web server

PHP (PHP-FPM):-Backend scripting language

MariaDB:-Database to store form data

PHP MySQL Connector (php-mysqlnd):-Connects PHP to MariaDB

HTML:-Signup form (frontend)

Git & GitHub:-version control and project hosting

# 🏗️ Architecture Diagram (AWS)


<img width="706" height="424" alt="WhatsApp Image 2026-10-22 at 3 19 50 PM" src="https://github.com/user-attachments/assets/08164c01-f19a-4796-af99-b94565de37eb" />

Flow: User → Internet → Security Group → Nginx → PHP-FPM → MariaDB → Response back to user.


# ⚙️ Setup & Installation (on EC2 Server)
Commands below are for Amazon Linux (ec2-user). Adjust the package manager if you use another OS.

Launch an EC2 instance AMI: Amazon Linux Instance type: t3.micro Security Group: allow SSH (22) and HTTP (80)
Connect to the server ssh -i my-key.pem ec2-user@
Install packages
sudo yum update

sudo yum install nginx mariadb105-server php -y

Start and enable services sudo systemctl enable nginx php-fpm mariadb
Create the database and table CREATE DATABASE FCT;
USE FCT;

CREATE TABLE users ( name VARCHAR(100), email VARCHAR(100), website VARCHAR(100), comment TEXT, gender VARCHAR(10));

Deploy the project cd /usr/share/nginx/html

clone the files sudo git clone https://github.com/Harshal2102/php-project.git

copy signup.html and submit.php into php-project/
Restart services sudo systemctl restart nginx php-fpm
Open in browser http:///php-project/signup.html
# 📥 Input
The user enters the following details in the Signup Form: Name Email Website Comment Gender (Female / Male / Other)
<img width="1920" height="1200" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/2a14d0ed-551f-41d2-aff3-40133077d0c4" />


# 📤 Output
After clicking Submit, submit.php saves the data and displays a success message with the submitted information.
<img width="1920" height="1200" alt="Screenshot (1)" src="https://github.com/user-attachments/assets/95bec6f9-3b86-4ec7-8ea2-0eadaf531949" />


# Data stored in MariaDB
The same data is verified in the database using: SELECT * FROM users;
<img width="1920" height="1200" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/b0442843-a795-4b24-8073-3199bea7c479" />


# ✅ Conclusion
In this project, a PHP application was successfully deployed on an AWS EC2 server using Nginx, PHP-FPM and MariaDB. The data entered in the signup form was stored correctly in the database and displayed back to the user, which confirms that the web server, PHP connector and database are all working together. Through this project I learned: Launching and configuring an EC2 instance and Security Group Installing and configuring Nginx, PHP and MariaDB on Linux Connecting PHP with a database using the MySQL connector Testing the full flow from the browser to the database Future improvements: use RDS for the database, add an Application Load Balancer, enable HTTPS with SSL, and add input validation and prepared statements for better security.

## 👤 Author
### Harshal Sonawane
