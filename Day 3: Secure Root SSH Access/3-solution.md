# Disable direct root login access

## Edit the sshd_config file
```
vi /etc/ssh/sshd_config

Edit the file and update the field PermitRootLogin to no
```
# Restart the sshd service
```
systemctl restart sshd
```
