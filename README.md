# Enumeration
NetBIOS Enumeration reveals Windows/Samba hostnames and workgroups using nmblookup -A &lt;IP>. Attackers use this to map network resources, identify file sharing services, and plan lateral movement within a network.

# **Challenge 1 — NetBIOS Enumeration**

Function : Queries a target's NetBIOS name table to reveal its hostname, workgroup/domain, and enabled network services (like file sharing).

Command :

nmblookup -A <target_IP>

Output :

<img width="446" height="241" alt="image" src="https://github.com/user-attachments/assets/18b77675-2259-4767-ba0a-48928b78844a" />


# **Challenge 2 — Fast Nmap Scan**

Function : Performs a fast scan of the top 100 most common ports on the target to quickly identify which network services are running.

Command :

nmap -F <target_IP>

Output :

<img width="582" height="467" alt="image" src="https://github.com/user-attachments/assets/2dbef082-285a-4f06-b281-1a40d21ded23" />


# **Challenge 3 — DNS Records**

Function : Queries DNS servers to retrieve domain records - ANY shows all records, MX finds mail servers, NS finds name servers, revealing a domain's infrastructure.

Command :

dig ANY <domain>

dig MX <domain>

dig NS <domain>

nslookup <domain>


Output :

Using dig (more detailed)

<img width="460" height="293" alt="image" src="https://github.com/user-attachments/assets/82210a71-f90c-4a1c-a201-3d22e4cbb6c3" />

Using nslookup

<img width="307" height="205" alt="image" src="https://github.com/user-attachments/assets/596083e4-7d63-44f7-8d56-441f7dc34492" />


# **Challenge 12 — Enum4linux (SMB Enumeration)**

Function : Comprehensive SMB enumeration tool that reveals target's OS, Samba version, user list, shared folders, workgroup name, and password policy in one command.

Command :

enum4linux -a <target_IP>

Output :

<img width="602" height="515" alt="image" src="https://github.com/user-attachments/assets/16c24964-ca9f-473b-8ea9-265339ba844d" />



# **Challenge 5 — TTL OS Fingerprinting**

Function :  Sends ICMP echo requests to test host connectivity and reveals operating system by analyzing TTL value in reply (64=Linux, 128=Windows).

Command :

ping <target_IP>

Output :

<img width="497" height="252" alt="image" src="https://github.com/user-attachments/assets/b9a6b0fd-ea81-4b56-88e5-72a4000801f3" />

# **Challenge 6 — Telnet Banner Grabbing**

Function : This command checks whether Telnet (port 23) is open on the target IP and identifies the service/version running on that port.

Command :

nmap -sV -p 23 <target_IP>

Output :

<img width="602" height="450" alt="image" src="https://github.com/user-attachments/assets/f228fa46-23d3-49f6-b684-43edc6c8cba9" />


# **Challenge 7 — HTTP Header Enumeration**

Function : Checks the target web server and displays its HTTP headers, server banner, and basic connection details for information gathering.

Command :

curl -I http://<target_IP>

curl -v http://<target_IP> 2>&1 | head -20

Output :

<img width="602" height="375" alt="image" src="https://github.com/user-attachments/assets/bb227b1b-b612-49d2-bec1-f10604aabca4" />


# **Challenge 8 — MySQL Enumeration**

Function : Scans port 3306 on the target IP to check if a MySQL database service is running and identifies its version.

Command :

nmap -sV -p 3306 <target_IP>

Output :

<img width="602" height="147" alt="image" src="https://github.com/user-attachments/assets/19bbceda-3efb-4708-a8aa-2d2f5343ba37" />


# **Challenge 9 — FTP Banner**

Function : Connects to port 21 (FTP) on the target IP using Netcat to check if the service is open and to view any FTP banner or response.

Command :

nc <target_IP> 21

Output :

<img width="345" height="72" alt="image" src="https://github.com/user-attachments/assets/eeb6b9b1-4bf6-4fd4-9983-9dd244c85004" />



# **Challenge 19 — RPC Info**

Function : Lists all available RPC services on the target IP, showing program numbers, versions, and ports to identify exposed network services.
Command :

rpcinfo -p <target_IP>

Output :

<img width="428" height="386" alt="image" src="https://github.com/user-attachments/assets/eb9f087d-2254-484d-a088-89531ea4a20b" />


