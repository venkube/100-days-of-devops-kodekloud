a. Install nginx on LBR (load balancer) server.


b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf.


c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers.


d. Once done, you can access the website using StaticApp button on the top bar.

### Install and Configure Nginx Load Balancer

### Install nginx
```
yum install nginx
```

### Configure Nginx to use as LB
#### Edit the default nginx conf located at /etc/nginx/nginx.conf
add the upstream app servers which need to add into LB under http context as below
```
http {

        upstream backend_servers {
          server        172.16.238.10:5002; #replace ip and port with your server ips and port
          server        172.16.238.11:5002;
          server        172.16.238.12:5002;
        }
```

### Now, update the same file for localtion proxy under server context
```
server{
  location / {
    proxy_pass http://backend_servers;  #refer to the same name as mentioned above
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
  }
}
```

### Login to each app server and check if apache i.e.. httpd is running and listening on the port mentioned
```
systemctl status httpd
```
