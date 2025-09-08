## SSL setup for Nginx

### Install the nginx
```
yum install nginx
```

### Start and enbled the nginx
```
systemctl enable nginx
systemctl start nginx
```

### To use the ssl, weneed to find the root directory of nginx
```
Edit the file /etc/nginx/nginx.conf
FInd the entry at down of file which was commented # Settings for a TLS enabled server
Uncomment all the fields under that and update the provided .crt and .key location entries.
        ssl_certificate "/etc/nginx/certs/nautilus.crt";
        ssl_certificate_key "/etc/nginx/certs/nautilus.key";
```

### Check the nginx configuration file for root directory
```
usually the root directory will be /usr/share/nginx/html
create a new index.html if not available or override with custom contents
```

### Restart the nginx
```
systemctl restart nginx
```

Go to Jump host and execute the command
```
curl  -k https://stapp02.stratos.xfusioncorp.com/
```
