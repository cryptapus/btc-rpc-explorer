### Setup of https://btc-explorer.com on Ubuntu 16.04

    apt update
    apt upgrade
    apt install git python-software-properties
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    npm install pm2 --global
    apt install nginx
    add-apt-repository ppa:certbot/certbot
    apt update
    apt upgrade
    apt install python-certbot-nginx
    
Copy content from [./btc-explorer.com.conf](./btc-explorer.com.conf) into `/etc/nginx/sites-available/btc-explorer.com.conf`

    certbot --nginx -d btc-explorer.com
    cd /etc/ssl/certs
    openssl dhparam -out dhparam.pem 4096
    cd /home/bitcoin/btc-rpc-explorer
    pm2 start bin/www --name "btc-rpc-explorer"