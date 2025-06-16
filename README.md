# Information-Gathering
Information Gathering - Passive &amp; Active

This project documents a full penetration testing cycle conducted in a controlled lab environment. 

The test covers everything from initial reconnaissance (Passive & Active), DNS enumeration, subdomain discovery, full port scans, and web technologies fingerprinting, to eventual system compromise via Telnet brute-force, reverse shell creation, and trace-cleaning.

 
**Scope:** Passive & Active Information Gathering → Exploitation → Post-Exploitation  
**Target:** `hackthebox.com`, IP `10.129.103.130`  
**Machine:** "MEOW" HTB Machine


## Tools & Techniques Used:

→ `ping`, `whois`, `dig`, `nslookup`, `host` → Basic recon
→ `Sublist3r` → Subdomain enumeration
→ `WhatWeb`, `WAFW00F` – Web technology & Firewall detection
→ `Nmap` – Full TCP SYN scan
→ `Telnet`, `Netcat`, `bash reverse shell` – Shell access & reverse connection
→ `Metasploit` – Automated Telnet login brute-force
→ `Hydra` – Credential brute-force (16 successful logins)
→ Manual post-exploitation (process listing, user enumeration, log clearing)


## Step-by-step attack:

### 1. Passive Recon

Results:

1. Collected WHOIS & DNS data on `hackthebox.com`
2. Detected Cloudflare protection, IP ranges, and name servers
3. Attempted (unsuccessful) Zone Transfer Attack
4. Used `Sublist3r` to find 48 subdomains (for example: `dev`, `api`, `cdn`, `status`)

### 2. Active Scanning:

1. `nmap` on IP `10.129.103.130` → Found open **Telnet (port 23)**
2. `WhatWeb` to fingerprint the site (Cloudflare, redirects, JS usage)

### 3. Exploitation:

Results:

a.) Gained shell access through Telnet → (`root:root`)
b.) Confirmed full system access on Ubuntu 20.04 LTS
c.) Used `Metasploit` to automate Telnet brute-force
d.) Used `Hydra` to discover 16 valid login pairs

### 4. Post-Exploitation:

a.) **Reverse Shell** using `bash` & `netcat`
b.) Verified root access, gathered `/etc/passwd`, checked processes
c.) Deleted `.bash_history`, logs (`auth.log`, `syslog`) & unset `HISTFILE`


## Access into the project:

*Written in Slovak language*

[Information_Gathering.pdf](./Information%20Gathering.pdf)

## 👨‍💻 Author:

Bc. Peter Mulik **(mulcb0t)**
