# Task 1.2: Automation L3.5 - Setup Sparta test app (with working posts page) on AWS using scripts (from Azure)

This document outlines the steps to set up the Sparta test app on AWS using scripts.

## Prerequisites

- Access to an AWS account
- Basic knowledge of AWS EC2 and shell scripting

## Steps

### 1. Create the Database VM

- Create an EC2 instance for the database server.
- Use the security group `tech241-<yourname>-db-sg-SSH-mongo` (or similar) for your security group name.
- Launch the instance and make a note of its public IP address.

### 2. Run the Database Script

- SSH into the database VM using the private key.
- Run the following script to set up the database:
```bash
#!/bin/bash
# Database script
# Update source list
sudo apt update -y

# Upgrade all the packages and install them in the kernel
sudo apt upgrade -y

# Import the MongoDB public GPG Key
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

# Create a list file for MongoDB
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# Reload local package database
sudo apt update -y

# Install MongoDB packages
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# Update the bindIp in mongod.conf
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf

# Start MongoDB
sudo systemctl start mongod

# Enable MongoDB to start on boot
sudo systemctl enable mongod
```
### 3. Check the Database Script

- Connect to the MongoDB instance on the database VM.
- Verify that the necessary collections and documents have been created.

### 4. Create the App VM

- Create another EC2 instance for the application server.
- Launch the instance and use an appropriate security group for the instance.

### 5. Run the App Script
```bash
#!/bin/bash
# App script
# Update source list
sudo apt update -y

# Upgrade all the packages and install them in the kernel
sudo apt upgrade -y

# Install nginx
sudo apt install nginx -y

# Start nginx on boot
sudo systemctl enable nginx

# Start nginx
sudo systemctl start nginx

# Add proxy command
sudo sed -i 's|try_files $uri $uri/ =404;|proxy_pass http://localhost:3000;|' /etc/nginx/sites-available/default

# Restart nginx
sudo systemctl restart nginx

# Enable nginx - auto runs on startup
sudo systemctl enable nginx

# Download Node.js
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

# Define the DB_HOST variable
export DB_HOST=172.187.178.145:27017/posts

# Install Node.js
sudo apt install nodejs -y

# Update source list
sudo apt update -y

# Install pm2
sudo npm install -g pm2

# Git clone app
git clone https://github.com/jungjinggg/tech241_sparta_app app-github-automation

# Get into app folder
cd ~/app-github-automation/app

# Install Node.js dependencies
npm install -y

# Start app
pm2 start app.js --name "sparta-app"

```

- SSH into the app VM using the private key.
- Run the app script to set up the application and reverse proxy.

### 6. Check the App Script

- Open a web browser and enter the public IP address of the app VM.
- Verify that the Sparta test app is accessible and functioning correctly.

---

Make sure to replace `<yourname>` with your actual name in the security group name. Run the database script on the database VM and the app script on the app VM. Verify the setup by checking the database and accessing the app via the public IP address.
