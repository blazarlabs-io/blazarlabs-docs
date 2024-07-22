# Server Setup

## Prerequisites

- Node JS [Install using nvm](https://github.com/nvm-sh/nvm)
- Npm (Installed along-side nvm node)
- Forever JS [Install via npm](https://www.npmjs.com/package/forever)
- Nginx [documentation](https://nginx.org/en/)
- Certbot [From Letsencrypt](https://letsencrypt.org/)

## Nginx

Nginx is used as a reverse proxy, this allows pointing multiple domain names to the same IP address and redirect each one to the corresponding node app.

### Nginx and Certbot Configuration

1. Update Ubuntu.

```
sudo apt update
```

2. Install Nginx

```
sudo apt install nginx
```

3. Adjust the Firewall

```
sudo ufw app list
```

You should see a result similar to:

```
Output
Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
```

Enable Nginx HTTP with the following command:

```
sudo ufw allow 'Nginx HTTP'
```

Verify your changes:

```
sudo ufw status
```

The output will indicated which HTTP traffic is allowed:

```
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
Nginx HTTP                 ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
```

4. Check Nginx status.

```
systemctl status nginx
```

The output should look like:

````
Output
● nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-04-20 16:08:19 UTC; 3 days ago
     Docs: man:nginx(8)
 Main PID: 2369 (nginx)
    Tasks: 2 (limit: 1153)
   Memory: 3.5M
   CGroup: /system.slice/nginx.service
           ├─2369 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           └─2380 nginx: worker process
           ```
````

5. Install Certbot.

```
sudo apt-get install certbot
```

6. Use certbot to obtain SSL certificate for each domain (app). Make sure you add the corresponding DNS A records pointing to the VPS public IP address. See the [Adding DNS records documentation](/add-dns-records) for more details.

```
sudo certbot certonly --nginx -d api.spiritsage.store
sudo certbot certonly --nginx -d api.blazarlabs.io
```

7. Configure Nginx as a Reverse Proxy.

Nginx will manage incoming requests and proxy them to the appropriate Node.js application based on the domain name.

Start by creating a new Nginx configuration file for each domain:

```
sudo nano /etc/nginx/sites-available/api.spiritsage.store
```

```
server {
    listen 80;
    server_name api.spiritsage.store;

    location / {
        return 301 https://$host$request_uri;
    }
}

server {
    listen 443 ssl;
    server_name api.spiritsage.store;

    ssl_certificate /etc/letsencrypt/live/api.spiritsage.store/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/api.spiritsage.store/privkey.pem;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

Save the file and create a symlink to enable the site:

```
sudo ln -s /etc/nginx/sites-available/api.spiritsage.store /etc/nginx/sites-enabled/
```

Test the configuration:

```
sudo nginx -t
```

Apply the new configuration by restarting Nginx:

```
sudo systemctl restart nginx
```
