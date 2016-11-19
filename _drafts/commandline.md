---
layout: page
title: Command Line
permalink: /notes/command-line
---

# Command Line

# Ubuntu Admin
###################

#Returns IP address and network information
ifconfig

# Launch Interactive Process Monitor for Server Monitoring
htop

# Launch Interactive Process Monitor for Server Monitoring (Simple; non-color)
top

# Check server memory
free -m

# Check Disk Space
df -h

# Returns Header Info
telnet IPADDRESS 80

# Update is used to resynchronize the package index files from their sources via Internet.
sudo apt-get update

# Upgrade is used to install the newest versions of all packages currently installed on the system
sudo apt-get upgrade

# Restart System
sudo reboot

# Locate a file
locate filename.log

###################
# Logging
###################

# Show first 100 mail transactions on server
sudo head -100 /var/log/mail.log

# Show first 100 older mail transactions on server
sudo head -100 /var/log/mail.log.1

# Show first 100 errors on server
sudo head -100 /var/log/nginx/error.log

# Show last 100 errors on server
sudo tail -100 /var/log/nginx/error.log

# Show errors on server in real time
sudo tail -f /var/log/nginx/error.log

# Show visitors info in real time
sudo tail -f /var/log/nginx/access.log

# List of modified files in the last 30 days
find /dir/here -type f -mtime -30

# Return the line where a string occurs in a file
sudo grep "string" /var/log/nginx/error.log

# Return the amount of times a string occurs in a file
sudo grep -c "string" /var/log/nginx/error.log

# Locate access.log ; Returns a list of directories where file exists
locate access.log # access.log is apache log file

# Show last 100 MYSQL errors on server
sudo tail -100 /var/log/mysqld.log

###################
# MYSQL
###################

# Enter mysql
mysql

# Show all databases within MYSQL prompt
mysql&gt; SHOW DATABASES;

# Create New Database within MYSQL prompt
mysql&gt; CREATE DATABASE database name;

# Switch to View Database
mysql&gt; USE database_name;

# Show tables of Database
mysql&gt; SHOW tables;

# Create New Database w/o entering MYSQL prompt
echo "create database wordpress_example_v1" | mysql -u root

# Export database to file w/o entering MYSQL prompt:
mysqldump -u username -p dbname &gt; sqlfile.sql

# Import database from file:
mysql -u username -p dbname &lt; sqlfile.sql

###################
# FTP
###################

# http://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users
cut -d: -f1 /etc/passwd # List all users
sudo adduser new_username # add a new user
sudo userdel username # remove/delete a user,