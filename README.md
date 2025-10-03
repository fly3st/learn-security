# Learn Security

I use this repository to store any notes, courses and links often related to offensive security / general fundementals I personally use.

## Basics / Fundementals

### Linux Essentials

**Core study**

* [Linux Foundation "Introduction to Linux (LFS101)"](https://training.linuxfoundation.org/training/introduction-to-linux/)
* [OverTheWire Bandit wargame](https://overthewire.org/wargames/bandit/)

**Hands-on**

* Bandit levels 0-25 w/ notes of commands
* Also run Linux on bare metal (Debian's your best bet)

### Bash (for PT)

**Core study**

* [Advanced Bash-Scripting Guide](https://tldp.org/LDP/abs/html/)
* [Bash scripting best practices](https://sap1ens.com/blog/2017/07/01/bash-scripting-best-practices/)
* [Bash quirks & safety](https://jvns.ca/blog/2017/03/26/bash-quirks/)
* [Text-tool primer](https://www-users.york.ac.uk/~mijp1/teaching/2nd_year_Comp_Lab/guides/grep_awk_sed.pdf)

**Hands-on**

* Nmap automation scripts
* Log summarizer pipline (`grep` + `awk` + `sort` etc..)

### Networking (for PT)

**Core study**

* [Practical Networking - “Networking Fundamentals / How data moves”](https://www.practicalnetworking.net/index/networking-fundamentals-how-data-moves-through-the-internet/)
* [TCM Security — “Networking Fundamentals for Pentesters”](https://tcm-sec.com/networking-fundamentals-for-pentesters/)
* [Practical Networking — Subnetting Mastery](https://www.practicalnetworking.net/stand-alone/subnetting-mastery)
* [Wireshark official / Wireshark sample captures](https://wiki.wireshark.org/samplecaptures)
* [UMass Kurose Wireshark labs](https://gaia.cs.umass.edu/kurose_ross/wireshark.php)
* [Cisco Packet Tracer](https://www.netacad.com/cisco-packet-tracer)
* [Scapy documentation](https://scapy.readthedocs.io/en/latest/usage.html)

**Hands-on**

* Use Wireshark + `tcpdump` and capture browser requests to `http://example.com` and filter `http` and follow the TCP stream
* Create 3 VMs in two different subnets and a Linux routing VM (make sure to enable `net.ipv4.ip_forward=1` and configure static routes and prove inter-subnet connectivity (`ping`,`traceroute`), use either Packet Tracer or GNS3 for virtual routers if you want to use a GUI
* Use `arp -a`, run an `arp-scan` in your lab and caputre ARP traffic using Wireshark
* Run full host-discovery + full port scan (`nmap -sS -p- -sV -O`) against lab hosts, save outputs and practice parsing results into attackable services (HTTP, SMB, SSH)
* Simulate a simple login POST on a test web app, capture the traffic (HTTP/S), show what metadata is visible with TLS, and extract URIs using `tshark`/Wireshark, also use the UMass Wireshark labs for guided exercises
* Write a small scapy script (see [Python](#python-for-pt)) that sends an ICMP echo request and prints the reply, also craft a SYN probe and observe replies in Wireshark
* Practice SSH local/remote port forwarding and dynamic SOCKS proxy: load a browser through an `ssh -D` SOCKS proxy and confirm traffic goes through the jump host
* Run Responder for LLMNR/NetBIOS poisoning to capture hashes, then crack them locally, make sure to understand mitigations (LLMNR off, SMB signing)

### Python (for PT)

**Core study**

* [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) (mostly focus on files, regex, web requests)
* [HTB Python 3 Module](https://academy.hackthebox.com/course/preview/introduction-to-python-3)

**Hands-on**

* Write either a port scanner, directory brute-forcer or a log parser (best if you can do all of 'em)
* Write an nmap automation script
* Write an ICMP probing script using scapy
* Read [impacket examples](https://github.com/fortra/impacket/tree/master/examples)

## Penetration Testing Specific

### Infra Pentesting (methodology focused)

**Core study**

* [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/PTES_Technical_Guidelines)
* [OWASP WSTG “Methodologies” section for test flow & reporting basics.](https://owasp.org/www-project-web-security-testing-guide/latest/3-The_OWASP_Testing_Framework/1-Penetration_Testing_Methodologies)
* [NIST SP 800-115 for formal test process](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-115.pdf)

**Hands-on**

* Practice recon (Nmap), service enum (banner grabbing), weak creds, and basic exploitation (Metasploit is fine). Use Nmap docs as your playbook.
* Write a PTES-style report w/ OWASP WSTG reporting guidance

### Linux PrivEsc

**Core study**

* [HTB Linux PrivEsc Course](https://academy.hackthebox.com/course/preview/linux-privilege-escalation)
* [g0tmi1k’s “Basic Linux Privilege Escalation”](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)
* [GTFOBins](https://gtfobins.github.io/)

**Hands-on**

* Go to [vulnhub](https://www.vulnhub.com/) and find yourself a linux VM (or just build a vulnerable one yourself) and use GTFOBins entries to go from user to root
* Make sure to enum -> identify -> exploit at least two distinct privesc paths (SUID + GUID) and a cron one as well. Document the exact GTFOBins snippets

### Windows PrivEsc

**Core study**

* [Absolomb’s Windows PrivEsc guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
* [HTB Windows PrivEsc Course](https://academy.hackthebox.com/course/preview/windows-privilege-escalation)
* [LOLBAS (learn Living-off-the-Land binaries) and its API](https://lolbas-project.github.io/)

**Hands-on**

* Practice service misconfigs, UAC bypasses, unquoted paths, AlwaysInstallElevated; reference LOLBAS entries during post-ex on a local Windows VM
* Escelate to admin using a documented vector and write a short playbook that consists of the commands used and an explanation of how and why they worked with a LOLBAS page citation.

### PowerShell (for PT)

**Core study**

* [Microsoft PowerShell docs](https://learn.microsoft.com/en-us/powershell/)
* [PowerSploit docs](https://powersploit.readthedocs.io/en/latest/)
* [PowerShell for Pentesters course material / repo](https://github.com/dievus/PowerShellForPentesters)

**Hands-on**

* Write a safe hello script and run it
* Write a local users & groups enum script

### AD (Active Directory)

**Core study**

* [HTB AD Course](https://academy.hackthebox.com/course/preview/active-directory-enumeration--attacks)
* [SpecterOps primers on AD attack paths & BloodHound](https://specterops.io/what-is-attack-path-management/)
* [HackTricks: AD Methodology](https://book.hacktricks.wiki/en/windows-hardening/active-directory-methodology/index.html)
* [HTB blog AD cheatsheet](https://www.hackthebox.com/blog/active-directory-penetration-testing-cheatsheet-and-guide)

**Hands-on**

* Build an AD lab and run BloodHound to map paths, practice Kerberoast, AS-REP roast, local admin spray, ADCS misconfig
* Produce a graph of one end-to-end attack path (user -> DC) and a step list (collection -> abuse -> persistence) w/ mitigations

### WebApp Pentesting

**Core study**

* [PortSwigger Academy - by far the best resource I've personally used](https://portswigger.net/web-security)
* [OWASP Web Security Testing Guide](https://nest.owasp.org/projects/web-security-testing-guide)
* [PayloadsAllTheThings repo](https://github.com/swisskyrepo/PayloadsAllTheThings)

**Hands-on**

* Complete PortSwigger Labs, they're great
* Self host practice apps like OWASP Juice Shop or DVWA

### App Pentesting

**Core study**

* [MAS Project](https://mas.owasp.org/MASTG/)
* [OWASP Mobile Application Security Testing Guide (MASTG)](https://owasp.org/www-project-mobile-app-security/)

**Hands-on**

* OWASP MAS Crackmes L1-L3, Triage with jadax, Frida and basic dynamic analysis
* Document one reversing path and one runtime-hooking bypass on a Crackme (screens + code snippets) w/ relevant MASTG section citation

**Each folder in the repo contains my personal notes on each subject, feel free to browse them or even correct me, I'm always learning.**
