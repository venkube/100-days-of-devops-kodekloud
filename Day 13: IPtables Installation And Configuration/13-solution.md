Install iptables on all hosts and block incoming 8083 port and allow only from lbhost.

Install iptables and its dependency services

```
sudo yum install -y iptables iptables-services
```

Enable and Start the iptables
```
systemctl start iptables
systemctl enable iptables
```

# Flush the existing rules
```
iptables -F
```

# Allow LB host
```
sudo iptables -A INPUT -p tcp -s $LB_IP --dport 8083 -j ACCEPT
```

# Drop all other traffic
```
sudo iptables -A INPUT -p tcp --dport 8083 -j DROP
```

# Save rules
```
systemctl iptables save
```

Note: Repeat the above process in all app hosts i.e.. stapp01, stapp02, stapp03
