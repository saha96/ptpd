# ptpd: how to test ptpd service on linux
This test was performed by Digt. (https://www.digt.ir/)
let's go

# install
First we need to install ptp daemon on Linux platform. I am using Ubuntu Server 18.04 for testing. 

sudo apt install ptpd 

# Server preparation
we need two servers that ping each other.

Server1:
saha@saha:~$ ifconfig
Ge0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.104  netmask 255.255.255.0  broadcast 192.168.1.255
        
Server2:
saha@saha:~$ ifconfig
MGMT1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.107  netmask 255.255.255.0  broadcast 192.168.1.255

Server1:
saha@saha:~$ ping 192.168.1.107
PING 192.168.1.107 (192.168.1.107) 56(84) bytes of data.
64 bytes from 192.168.1.107: icmp_seq=1 ttl=64 time=0.087 ms
64 bytes from 192.168.1.107: icmp_seq=2 ttl=64 time=0.088 ms
^C
--- 192.168.1.107 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1028ms
rtt min/avg/max/mdev = 0.087/0.087/0.088/0.009 ms

Server2:
saha@saha:~$ ping 192.168.1.104
PING 192.168.1.104 (192.168.1.104) 56(84) bytes of data.
64 bytes from 192.168.1.104: icmp_seq=1 ttl=64 time=0.141 ms
64 bytes from 192.168.1.104: icmp_seq=2 ttl=64 time=0.105 ms
^C
--- 192.168.1.104 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1008ms
rtt min/avg/max/mdev = 0.105/0.123/0.141/0.018 ms

# configuration
Just use the configuration files provided in this directory on the two servers or servers under test.

# test
Coming soon...
