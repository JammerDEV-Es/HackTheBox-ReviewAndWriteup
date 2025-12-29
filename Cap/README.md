# Cap (Easy) 🟢
<div align="center">
</div>
<img width="256" height="256" src="https://github.com/JammerDEV-Es/HackTheBox-ReviewAndWriteup/blob/main/Cap/Images/Cap.png">
</p>

## This machine was really easy. After completing other, more complex ones, this one felt like a gift.
The first step is the recognition phase:
```bash
nmap -sS -vvv --min-rate 5000 -Pn -p- --open -n 10.10.11.59 -oG allPorts
```
The scan reports the following:
```bash
# Nmap 7.95 scan initiated Mon Dec 29 11:01:29 2025 as: /usr/lib/nmap/nmap --privileged -sS -vvv -p- --open -n -Pn --min-rate 5000 -oG allPorts 10.10.10.245
# Ports scanned: TCP(65535;1-65535) UDP(0;) SCTP(0;) PROTOCOLS(0;)
Host: 10.10.10.245 ()   Status: Up
Host: 10.10.10.245 ()   Ports: 21/open/tcp//ftp///, 22/open/tcp//ssh///, 80/open/tcp//http///   Ignored State: closed (65532)
# Nmap done at Mon Dec 29 11:01:42 2025 -- 1 IP address (1 host up) scanned in 13.24 seconds
```
Ports `21`, `22`, and `80` are open, which means that `FTP`, `SSH`, and `HTTP` services are active.

So let's learn more about these TCP ports:
```bash
nmap -sCV -p21,22,80 10.10.10.245 -oN targeted

```
The scan will reports the following:
```bash
# Nmap 7.95 scan initiated Mon Dec 29 11:03:06 2025 as: /usr/lib/nmap/nmap --privileged -sCV -p21,22,80 -oN targeted 10.10.10.245
Nmap scan report for cap.htb (10.10.10.245)
Host is up (0.059s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 fa:80:a9:b2:ca:3b:88:69:a4:28:9e:39:0d:27:d5:75 (RSA)
|   256 96:d8:f8:e3:e8:f7:71:36:c5:49:d5:9d:b6:a4:c9:0c (ECDSA)
|_  256 3f:d0:ff:91:eb:3b:f6:e1:9f:2e:8d:de:b3:de:b2:18 (ED25519)
80/tcp open  http    Gunicorn
|_http-server-header: gunicorn
|_http-title: Security Dashboard
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Dec 29 11:03:17 2025 -- 1 IP address (1 host up) scanned in 10.21 seconds
```
At first glance we can see a service to exploit with the CVE which would be `vsftpd 3.0.3` but it would be to carry out a DDoS attack which is not of interest to us.

And little else we can see by putting the following in the `Launchpad` would be that this `OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)` comes from a `Focal` machine.

#

So after all this, we'll go to the page. We can see several sections: `/ip`, `/netstat`, and `/capture`, which is the one we're interested in. We'll click on it and have to wait approximately 5 seconds for it to take the Security Snapshot. 

It will redirect us to a page with a subdirectory called `/data/(int)`. Within that int value, it will take you to a random one, and you can download it below in .pcap format. 

So, we're going to start (and finish) from the first one. We'll enter /data/0 and download the .pcap file.
