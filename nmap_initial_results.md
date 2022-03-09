# nmap\_initial\_results

**knowledge\_check\_initial\_scan.gnmap**

```bash
# Nmap 7.92 scan initiated Tue Mar  8 12:22:22 2022 as: nmap -sV --open -oA knowledge_check_initial_scan 10.129.164.26

Host: 10.129.164.26 ()	Status: Up

Host: 10.129.163.1 ()	Ports: 22/open/tcp//ssh//OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)/, 80/open/tcp//http//Apache httpd 2.4.41 ((Ubuntu))/

# Nmap done at Tue Mar  8 12:22:51 2022 -- 1 IP address (1 host up) scanned in 29.14 seconds
```

**knowledge\_check\_initial\_scan.nmap**

```bash
# Nmap 7.92 scan initiated Tue Mar  8 12:22:22 2022 as: nmap -sV --open -oA knowledge_check_initial_scan 10.129.164.26

Nmap scan report for 10.129.164.26

Host is up (0.22s latency).

Not shown: 753 closed tcp ports (conn-refused), 245 filtered tcp ports (no-response)

Some closed ports may be reported as filtered due to --defeat-rst-ratelimit

PORT   STATE SERVICE VERSION

22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)

80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel



Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .

# Nmap done at Tue Mar  8 12:22:51 2022 -- 1 IP address (1 host up) scanned in 29.14 seconds
```

**knowledge\_check\_initial\_scan.xml**

```xml
 cpe:/a:openbsd:openssh:8.2p1cpe:/o:linux:linux_kernel cpe:/a:apache:http_server:2.4.41 
```
