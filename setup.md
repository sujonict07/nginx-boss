
### Install and configurations(Ubuntu-18.04): 

```
sudo apt update
sudo apt install nginx
```

# Adjusting the Firewall
```
sudo ufw app list
sudo ufw allow 'Nginx HTTP'
sudo ufw status
```
# start nginx 
```
sudo systemctl start nginx
systemctl status nginx
systemctl restart nginx
sudo systemctl stop nginx
# If you are simply making configuration changes,
# Nginx can often reload without dropping connections. 
# To do this, type:
sudo systemctl reload nginx
sudo systemctl disable nginx
sudo systemctl enable nginx
```

## configurations setup
```
Nginx configurations : 
sudo vim /etc/nginx/sites-available/shifu_staging.com
server {
    listen 80;
    server_name <Server_ip>;
    location / {
    root <base_location>/kutumbita-web/build;
        index index.html index.htm;
        try_files $uri $uri/ /index.html;
    }
    
    location /api {
       proxy_pass http://<Server_ip>:5000;
    }
    
    location /android {
       proxy_pass http://<Server_ip>:5100;
    }
}
# enable the file by creating a link from it to the 'site-enable' directory which 
nginx reads from during startup:
sudo ln -s /etc/nginx/sites-available/shifu_staging.com /etc/nginx/sites-enabled/
# To show your configuration files:
sudo vim /etc/nginx/nginx.conf
# To make sure that there are no syntax errors:
```

### nginx common commands
```
sudo nginx -t
# Finish!! Lets go to deploy kutumbita-web
# Go to kutumbita-web repository
For Web:
#Configuration and setup npm
    npm install
    npm run build

```
