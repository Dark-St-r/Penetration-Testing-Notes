# ls
This command lists all the contents of a directory.
Usage Example: ls

# Nmap
Nmap is a free and open-source network scanner created by Gordon Lyon. Nmap is used to discover hosts and services on a computer network by sending packets and analyzing the responses. Nmap provides a number of features for probing computer networks, including host discovery and service and operating system detection.

Nmap allows you to scan your network and discover not only everything connected to it, but also a wide variety of information about what's connected, what services each host is operating, and so on. It allows a large number of scanning techniques, such as UDP, TCP connect (), TCP SYN (half-open), and FTP.
Usage Exmaple: sudo nmap -sV {IP Address}

-sV is a service detection flag used to determine the name and description of the identified services. 

# telnet
This is an application protocal used on the internet or local accesss network(LAN) to provide bidirectional interactive text-oriented communication facility using a virtual terminal connection. Telnet is an old service used for remote management of other hosts on the network.
Usage Example: telnet {target_ip}

# cat
This command is used to read files from a terminal.
Usage Example: cat flag.txt

# ftp
See [FTP](https://github.com/Dark-St-r/Penetration-Testing-Notes/blob/99a30bafac9ce46a5865459bbefc64f594035ab4/useful-notes.md#L1) for more information on it.
Usage Example: ftp -h

# man
Allows for finding more detail abou ta specific command.
Usage Example: man {commandname}

# cd
Allows for the accessing of directories.
Usage Example: cd {directory-locaton}

# get
Used to get a file from ftp server.
Usage Example: get {filename}

# smbclient
An SMB client is the device that accesses resources on an SMB server. For example, within a corporate network, the user PCs that access a shared drive are SMB clients.
Usage Example: smbclient -L {target_ip} && smbclient \\\\{target_ip}\\{accountname}
-L is used to list.

# xfreerdp
FreeRDP is a free implementation of the Remote Desktop Protocol (RDP), released under the Apache license. Enjoy the freedom of using your software wherever you want, the way you want it, in a world where interoperability can finally liberate your computing experience.
Usage Example: xfreerdp /v:{target_ip} /cert:ignore /u:Administrator

# gobuster
Gobuster v3.1.0. Gobuster is a tool used to brute-force: URIs (directories and files) in web sites. DNS subdomains (with wildcard support).
Usage Example: gobuster -h