## Tasks

###### Task 1

What does the 3-letter acronym FTP stand for?

[File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol)
###### Task 2

Which port does the FTP service listen on usually?

[Port: 21](https://www.speedguide.net/port.php?port=21)

###### Task 3

FTP sends data in the clear, without any encryption. What acronym is used for a later protocol designed to provide similar functionality to FTP but securely, as an extension of the SSH protocol?

[SFTP](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)

###### Task 4

What is the command we can use to send an ICMP echo request to test our connection to the target?

[ping](https://en.wikipedia.org/wiki/Ping_(networking_utility))

###### Task 5

From your scans, what version is FTP running on the target? 

[vsftpd 3.0.3](https://en.wikipedia.org/wiki/Vsftpd#:~:text=vsftpd%20(or%20very%20secure%20FTP,Slackware%20and%20RHEL%20Linux%20distributions. )

###### Task 6

From your scans, what OS type is running on the target?

[Unix](https://en.wikipedia.org/wiki/Unix)

###### Task 7

What is the command we need to run in order to display the 'ftp' client help menu? 

[ftp -h](https://www.commandlinux.com/man-page/man1/ftp.1.html)

###### Task 8

What is username that is used over FTP when you want to log in without having an account? 

[anonymous](https://en.wikipedia.org/wiki/File_Transfer_Protocol#Anonymous_FTP)

###### Task 9

What is the response code we get for the FTP message 'Login successful'? 

[230](https://en.wikipedia.org/wiki/List_of_FTP_server_return_codes)

###### Task 10

There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.

[ls](https://en.wikipedia.org/wiki/Ls)

###### Task 11

What is the command used to download the file we found on the FTP server? 

[get](https://wiki.gentoo.org/wiki/FTP#Usage)

## Flags
Ping the target machine and run a service version port scan using nmap
```shell
[cry_baby@ace ~]$ ping 10.129.98.211
PING 10.129.98.211 (10.129.98.211) 56(84) bytes of data.
64 bytes from 10.129.98.211: icmp_seq=1 ttl=63 time=14.5 ms
64 bytes from 10.129.98.211: icmp_seq=2 ttl=63 time=13.6 ms
64 bytes from 10.129.98.211: icmp_seq=3 ttl=63 time=10.8 ms
64 bytes from 10.129.98.211: icmp_seq=4 ttl=63 time=12.2 ms
^C
--- 10.129.98.211 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 10.846/12.778/14.529/1.393 ms
[cry_baby@ace ~]$ nmap -sV 10.129.98.211
Starting Nmap 7.95 ( https://nmap.org ) at 2024-08-15 02:19 EDT
Nmap scan report for 10.129.98.211
Host is up (0.012s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 0.33 seconds
```
From the nmap results we can see a ftp servicee running on port 21, so lets try cone
```shell
[cry_baby@ace ~]$ ftp 10.129.98.211
Connected to 10.129.98.211.
220 (vsFTPd 3.0.3)
Name (10.129.98.211:cry_baby):
```
Login using anonymous and login without a password
```shell
Name (10.129.98.211:cry_baby): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```
list all the files and download the flag.txt on to your machine
```shell
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
226 Directory send OK.
ftp> get flag.txt
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for flag.txt (32 bytes).
226 Transfer complete.
32 bytes received in 0.00186 seconds (16.8 kbytes/s)
ftp> quit
221 Goodbye.
[cry_baby@ace ~]$ ls
 flag.txt
[cry_baby@ace ~]$ cat flag.txt
035db21c881520061c53e0536e44f815
[cry_baby@ace ~]$ 
```





















