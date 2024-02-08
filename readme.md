# Setting Up a LAMP Server on AWS

## Introduction

This guide provides a concise overview of setting up a LAMP (Linux, Apache, MySQL, PHP) server on Amazon Web Services (AWS). It outlines the steps required to deploy a WordPress website on the server.

## Steps:

1. **Create an AWS Account:**
    - Sign up for an AWS account if you haven't already.

2. **Launch an EC2 Instance:**
    - Log in to the AWS Management Console.
    - Navigate to the EC2 service.
    - Click on "Launch Instance" to choose an Amazon Machine Image (AMI) for your server. Select a suitable Linux distribution.
    - Configure instance details, such as instance type, network settings, and security groups.
    - Review and launch the instance.

3. **Connect to the EC2 Instance:**
    - Use SSH to connect to the newly launched EC2 instance from your local machine.
    ```
    ssh -i <your_key.pem> ec2-user@<public_ip_address>
    ```
    Replace `<your_key.pem>` with the path to your private key file and `<public_ip_address>` with the public IP address of your EC2 instance.

4. **Install LAMP Stack:**
    - Update the package index on the EC2 instance.
    ```
    sudo apt update
    ```
    - Install Apache, MySQL, and PHP packages using the package manager (e.g., apt-get for Ubuntu).
    ```
    sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
    ```
    - Secure MySQL installation and set up a MySQL root password.
    ```
    sudo mysql_secure_installation
    ```

5. **Install WordPress:**
    - Download the latest version of WordPress from the official website.
    ```
    wget https://wordpress.org/latest.tar.gz
    ```
    - Extract the WordPress archive and move it to the Apache web root directory.
    ```
    tar -zxvf latest.tar.gz
    sudo mv wordpress/* /var/www/html/
    ```
    - Create a MySQL database and user for WordPress.
    ```
    sudo mysql -u root -p
    ```
    ```
    CREATE DATABASE wordpress;
    CREATE USER 'wordpress_user'@'localhost' IDENTIFIED BY 'password';
    GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress_user'@'localhost';
    FLUSH PRIVILEGES;
    EXIT;
    ```
    - Configure WordPress to connect to the MySQL database. 
    - Complete the WordPress installation through the web browser by accessing your EC2 instance's public IP address.

6. **Access WordPress:** 
    - Once WordPress is installed, access the WordPress admin dashboard using the public IP address of your EC2 instance.
    - Complete the setup process and begin customizing your WordPress website.
  
## Conclusion

This guide has provided a straightforward approach to setting up a LAMP server on AWS and deploying WordPress. By following these steps, users can quickly establish a reliable hosting environment for their websites or web applications on the AWS cloud infrastructure.

