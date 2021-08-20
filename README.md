# ptpd: how to test ptpd service on linux
This test was performed by Digt.

let's go

# install
First we need to install ptp daemon on Linux platform. I am using Ubuntu Server 18.04 for testing. 

```
sudo apt install ptpd 
```

# Server preparation
we need two servers that ping each other.

```
saha@server1:~$ ifconfig

Ge0: inet 192.168.1.104  netmask 255.255.255.0  broadcast 192.168.1.255
```

```
saha@server2:~$ ifconfig

MGMT1: inet 192.168.1.107  netmask 255.255.255.0  broadcast 192.168.1.255
```

# configuration
Just use the configuration files provided in this directory on the two servers or servers under test.

# test

First we review configuration file
```
sudo vim /etc/ptpd.conf
```
Next we make sure that protocol is disabled
```
sudo service ptpd stop
sudo service ptpd status
```
To ensure service is active, we can use the following commands
```
sudo pkill ptpd; sudo service ptpd stop; sudo /usr/sbin/ptpd -c /etc/ptpd.conf 2>/dev/null; sudo service ptpd start
```
We use following commands to ensure that ntp protocol and timesync daemon is disabled  
```
sudo timedatectl set-ntp no ; sudo systemctl stop systemd-timesyncd.service
```
We use following command to display system clock in detail
```
timedatectl
```
View protocol logs
```
sudo cat /var/log/ptpd2.log | tail -n 10
```
To change the clock
```
sudo date +%T -s "11:17:00" ; sudo hwclock -w
```
View messages sent from master to Slave.

And we will see that time difference is decreasing.
```
sudo cat /var/log/ptpd2.stats | tail -n 10
```
When we're done, we reactivate services
```
sudo timedatectl set-ntp yes ; sudo systemctl start systemd-timesyncd.service
```

# More information

coming soon ...
