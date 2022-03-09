#### My findings after running the **http-enum** script.

```bash
# Nmap 7.92 scan initiated Tue Mar  8 09:34:23 2022 as: nmap -sV --script=http-enum -oA knowledge_check_http_enum 10.129.164.26

Nmap scan report for 10.129.164.26

Host is up (0.17s latency).

Not shown: 998 closed tcp ports (conn-refused)

PORT   STATE SERVICE VERSION

22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)

80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))

| http-enum: 

|   /admin/: Possible admin folder

|   /admin/index.php: Possible admin folder

|   /backups/: Backup folder w/ directory listing

|   /robots.txt: Robots file

|_  /data/: Potentially interesting directory w/ listing on 'apache/2.4.41 (ubuntu)'

|_http-server-header: Apache/2.4.41 (Ubuntu)

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel



Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .

# Nmap done at Tue Mar  8 09:35:24 2022 -- 1 IP address (1 host up) scanned in 61.67 seconds


```
