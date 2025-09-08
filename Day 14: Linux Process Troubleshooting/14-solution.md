# Verify Linux process and Port Binding

### to check for existing process running on server use below command
```
sudo netstat -tulnp
```
It displays all the running process with port numbers. Identify it and kill it if needed using command
```
kill -9 <process_id>
```

For this solution, if apache throws error like below or unable to start the apache
```
98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:6000
```
#### check the apache status
```
systemctl status httpd
systemctl start httpd
```

### To check which port is currently in use for apache
```
apachectl -S
which displays apache configuration and root path
```

### Go to /etc/httpd/conf/httpd.conf file and check for the field LISTEN
Make sure the correct port is set as mentioned in question.
