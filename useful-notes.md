# FTP
The File Transfer Protocol (FTP) is a standard communication protocol used to transfercomputer files from a server to a client on a computer network. FTP is built on aclient–server model architecture using separate control and data connections betweenthe client and the server. FTP users may authenticate themselves with a clear-textsign-in protocol, generally in the form of a username and password. However, they canconnect anonymously if the server is configured to allow it. For secure transmissionthat protects the username and password and encrypts the content, FTP is often securedwith SSL/TLS (FTPS) or replaced with SSH File Transfer Protocol (SFTP).

# SMB (Server Message Block)
This communication protocol provides shared access to files, printers, and serial ports between endpoints on a network.
In computer networking, Server Message Block, one version of which was also known as Common Internet File System, is a communication protocol for providing shared access to files and printers between nodes on a network. It also provides an authenticated inter-process communication mechanism.

# RDP (Remote Desktop Protocol)
Operates on ports *3389 TCP* and *3389 UDP*. The only difference consists of how the information relayed by this protocol is presented to the end-user.

# SSH (Secure Shell Protocol)
Adds the required layers of authentication and encryption to the communication model, making it a much more viable approach to perform remote access and remote file transfers. It is used both for patch delivery, file transfers, log transfer, and remote management.
SSH uses public-key cryptography to verify the remote host's identity, and the communication model is based on the Client-Server architecture, as seen previously with FTP, SMB, and other services. The local host uses the server's public key to verify its identity before establishing the encrypted tunnel connection. Once the tunnel is established, symmetric encryption methods and hashing algorithms are used to ensure the confidentiality and integrity of the data being sent over the tunnel.