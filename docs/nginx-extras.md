# Nginx Extras

To stop your web server, type:

```bash
sudo systemctl stop nginx
```

To start the web server when it is stopped, type:

```bash
sudo systemctl start nginx
```

To stop and then start the service again, type:

```bash
sudo systemctl restart nginx
```

If you are only making configuration changes, Nginx can often reload without dropping connections. To do this, type:

```bash
sudo systemctl reload nginx
```

By default, Nginx is configured to start automatically when the server boots. If this is not what you want, you can disable this behavior by typing:

```bash
sudo systemctl disable nginx
```

To re-enable the service to start up at boot, you can type:

```bash
sudo systemctl enable nginx
```
