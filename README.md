<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>

  <p align="center">A progressive <a href="http://nodejs.org" target="blank">Node.js</a> framework for building efficient and scalable server-side applications, heavily inspired by <a href="https://angular.io" target="blank">Angular</a>.</p>
  
</p>

# HERE IS THE BASH SCRIPT THAT IS USED IN THIS TASK👇
 
```
#!/bin/bash

# Update and upgrade packages
sudo apt-get update -y
sudo apt-get upgrade -y

# Install essential packages
sudo apt-get install -y build-essential
sudo apt-get install -y nginx

# Clone the GitHub repository
git clone https://github.com/VinodPandhare/internshiptask1

# Install NVM (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Source NVM script to ensure 'nvm' command is available in the current session
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

# Install the latest LTS version of Node.js
nvm install --lts

# Change to the project directory
cd internshiptask1

# Install npm dependencies and build the project
npm i
npm run build

# Go back to the home directory
cd ~

# Configure Nginx
sudo bash -c 'cat > /etc/nginx/sites-available/demo <<EOF
server {
    # Listen on port 80 (HTTP)
    listen 80;

    # Server name (domain or subdomain)
    server_name 3.16.166.179; #REPLACEWITHYOURACTUALIP

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade \$http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host \$host;
        proxy_cache_bypass \$http_upgrade;
    }
}
EOF'

# Enable the new Nginx configuration
sudo ln -s /etc/nginx/sites-available/demo /etc/nginx/sites-enabled/

# Install PM2 globally
npm install -g pm2

# Start the application using PM2
cd ~/internshiptask1
pm2 start dist/main.js --name "nestjs-app"
pm2 save
pm2 startup

# Test the Nginx configuration and restart Nginx
sudo nginx -t
sudo systemctl restart nginx

# Allow Nginx through the firewall and enable it
sudo ufw allow 'Nginx Full'
sudo ufw enable


```




