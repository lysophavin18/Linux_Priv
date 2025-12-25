# 🐧 Linux Privilege Escalation

> Practical notes, tools, and references for Linux enumeration and privilege escalation  
> Built from hands-on labs, CTFs, and security courses.

---

## 🎯 Objectives

- Understand Linux privilege escalation fundamentals  
- Practice **manual & automated enumeration**
- Identify **misconfigurations, weak permissions, and kernel vulnerabilities**
- Apply techniques in **TryHackMe, labs, and CTF environments**

---

## 📚 Learning Resources

- **g0tmi1k – Basic Linux Privilege Escalation**  
  https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

- **PayloadsAllTheThings – Linux PrivEsc**  
  https://github.com/swisskyrepo/PayloadsAllTheThings

- **HackTricks – Linux PrivEsc Checklist**  
  https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist

- **Sushant 747 – OSCP Linux Guide**  
  https://sushant747.gitbooks.io/total-oscp-guide/

- **All-in-One Resource Repository**  
  https://github.com/Gr1mmie/Linux-Privilege-Escalation-Resources

---

## 🧪 Labs & Practice

- **TryHackMe – Linux PrivEsc Arena**  
  https://tryhackme.com/room/linuxprivescarena

- **Linux PrivEsc Playground**  
  https://tryhackme.com/room/privescplayground

- **TryHackMe Platform**  
  https://tryhackme.com/

---

## 🛠️ Enumeration Tools

| Tool | Purpose |
|-----|--------|
| LinPEAS | Automated privilege escalation checks |
| LinEnum | Lightweight enumeration |
| Linux Exploit Suggester | Kernel exploit discovery |
| Linux Priv Checker | Permission & config analysis |

---

## 🔍 Core Enumeration Commands

```bash
hostname
uname -a
cat /etc/issue
ps aux
env
sudo -l
id
history
