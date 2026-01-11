# Gavel (Medium) 🟠
<div align="center">
</div>
<img width="256" height="297" src="https://github.com/JammerDEV-Es/HackTheBox-ReviewAndWriteup/blob/main/Gavel/Images/gavel.png">
</p>

#
Let's get straight to start the reconnaissance phase:
```bash
nmap -sS -vvv -p- --open -n -Pn --min-rate 5000 10.10.11.97 -oG allPorts 
```
```java

# Nmap 7.98 scan initiated Sun Jan 11 14:32:36 2026 as: /usr/lib/nmap/nmap --privileged -sS -vvv -p- --open -n -Pn --min-rate 5000 -oG allPorts 10.10.11.97
# Ports scanned: TCP(65535;1-65535) UDP(0;) SCTP(0;) PROTOCOLS(0;)
Host: 10.10.11.97 ()    Status: Up
Host: 10.10.11.97 ()    Ports: 22/open/tcp//ssh///, 80/open/tcp//http///    Ignored State: closed (65533)
# Nmap done at Sun Jan 11 14:32:49 2026 -- 1 IP address (1 host up) scanned in 13.30 seconds
```
The page tells us that it has port 22 and port 80 open, so the active services are HTTP and SSH.
