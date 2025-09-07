# Install and Configure the SELinux

## Install the required SELinux packages
```
sudo yum install -y policycoreutils selinux-policy selinux-policy-targeted
```

## Edit the SELinux config file:
```
sudo vi /etc/selinux/config
```

## Change the Line to SELINUX=disabled

check the status
```
[root@stapp02 steve]# sestatus
SELinux status:                 disabled
```

## to temporarily disable, we can do without reboot using command
```
sudo setenforce 0
getenforce
```
