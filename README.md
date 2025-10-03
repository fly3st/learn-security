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

### Python (for PT)

**Core study**

* [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) (mostly focus on files, regex, web requests)
* [HTB Python 3 Module](https://academy.hackthebox.com/course/preview/introduction-to-python-3)

**Hands-on**

* Write either a port scanner, directory brute-forcer or a log parser (best if you can do all of 'em)

### Infra Pentesting (methodology focused)

**Core study**

* [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/PTES_Technical_Guidelines)
* [OWASP WSTG “Methodologies” section for test flow & reporting basics.](https://owasp.org/www-project-web-security-testing-guide/latest/3-The_OWASP_Testing_Framework/1-Penetration_Testing_Methodologies)
* [NIST SP 800-115 for formal test process](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-115.pdf)

**Hands-on**

* Practice recon (Nmap), service enum (banner grabbing), weak creds, and basic exploitation (Metasploit is fine). Use Nmap docs as your playbook.
* Write a PTES-style report w/ OWASP WSTG reporting guidance

### Windows PrivEsc

**Core study**

* [Absolomb’s Windows PrivEsc guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
* [HTB Windows PrivEsc Course](https://academy.hackthebox.com/course/preview/windows-privilege-escalation)
* [LOLBAS (learn Living-off-the-Land binaries) and its API](https://lolbas-project.github.io/)

**Hands-on**

* Practice service misconfigs, UAC bypasses, unquoted paths, AlwaysInstallElevated; reference LOLBAS entries during post-ex on a local Windows VM
* Escelate to admin using a documented vector and write a short playbook that consists of the commands use and an explanation of how and why they worked with a LOLBAS page citation.

### Linux PrivEsc

**Core study**

* [HTB Linux PrivEsc Course](https://academy.hackthebox.com/course/preview/linux-privilege-escalation)
* [g0tmi1k’s “Basic Linux Privilege Escalation”](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)
* [GTFOBins](https://gtfobins.github.io/)

**Hands-on**

* Go to [vulnhub)(https://www.vulnhub.com/) and find yourself a linux VM (or just build a vulnerable one yourself) and use GTFOBins entries to go from user to root
* Make sure to enum -> identify -> exploit at least two distinct privesc paths (SUID + GUID) and a cron one as well. Document the exact GTFOBins snippets

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


