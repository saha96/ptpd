# ptpd: how to test ptpd service on linux
This test was performed by Digt. (https://www.digt.ir/)

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
Coming soon...
