Installation Guide for Apache, MySQL, and phpMyAdmin

This guide provides step-by-step instructions using bash scripting to install and configure the essential LAMP (Linux, Apache, MySQL, PHP) components: Apache web server, MySQL database server, and phpMyAdmin for database management.

Prerequisites

A Linux system with root or sudo privileges
Basic familiarity with bash scripting
Installation Script

Save the following script as install_lamp.sh and make it executable with chmod +x install_lamp.sh:

Bash
#!/bin/bash

# Update package lists
sudo apt update

# Install Apache2
echo "Installing Apache2..."
sudo apt install apache2 -y

# Start Apache2 service
echo "Starting Apache2..."
sudo systemctl start apache2

# Enable Apache2 to start automatically at boot
echo "Enabling Apache2 on boot..."
sudo systemctl enable apache2

# Install MySQL
echo "Installing MySQL..."
sudo apt install mysql-server -y

# Secure MySQL installation
echo "Securing MySQL..."
sudo mysql_secure_installation

# Install phpMyAdmin
echo "Installing phpMyAdmin..."
sudo apt install phpmyadmin -y

# Enable phpMyAdmin configuration
echo "Enabling phpMyAdmin..."
sudo a2enconf phpmyadmin.conf

# Restart Apache2 to apply changes
echo "Restarting Apache2..."
sudo systemctl restart apache2

# Display success message
echo "LAMP stack (Apache, MySQL, phpMyAdmin) successfully installed!"
Use code with caution.
Explanation of the Script

Update package lists: Ensures access to the latest package information.
Install Apache2: Downloads and installs the Apache web server.
Start Apache2 service: Initiates the Apache service.
Enable Apache2 on boot: Configures Apache to start automatically when the system boots.
Install MySQL: Downloads and installs the MySQL database server.
Secure MySQL installation: Runs the mysql_secure_installation script to set a strong root password and configure other security settings.
Install phpMyAdmin: Downloads and installs the phpMyAdmin web interface for managing MySQL databases.
Enable phpMyAdmin configuration: Links the phpMyAdmin configuration file to Apache, making it accessible through a web browser.
Restart Apache2: Restarts Apache to apply the changes made by enabling phpMyAdmin.
Display success message: Informs the user of the successful installation.
Accessing phpMyAdmin

Open a web browser and navigate to http://localhost/phpmyadmin.
Use the root password you set during the MySQL installation to log in.
Additional Considerations

Firewall Rules: If a firewall is running, you may need to open ports 80 (HTTP) and 3306 (MySQL) for external access. Consult your firewall documentation for specific instructions.
Security Practices: Always adhere to security best practices when setting up LAMP components. Use strong passwords, disable unnecessary features, and keep software updated.
Customization: You can customize the script to adjust settings based on your specific needs. Research for additional configurations on the official documentation of Apache, MySQL, and phpMyAdmin.
