Exercise 1: 
Description:
	The tool used for port-scanning is Nmap 7.80 (Network Mapper). It is a free open-source tool for vulnerability scanning and network discovery. This tool is also helpful in monitoring host or service uptime and can also perform mapping of network attack surfaces. Nmap runs on all the major operating systems and is suitable for scanning both large & small networks. It gathers information by sending raw packets to system ports. It listens for responses and determines whether ports are open, closed or filtered. 
Nmap employs transport layer protocols including TCP (Transmission Control Protocol), UDP (User Datagram Protocol), and SCTP (Stream Control Transmission Protocol) as well as supporting protocols like ICMP (Internet Control Message Protocol), used to send error message.
 
Installation of Nmap on Windows: 
-	Nmap can be easily installed from its official website https://nmap.org/download.html.
-	Run the downloaded .exe file. In the window that opens, accept the license terms.
-	Choose the components to install. By default, the Zenmap GUI will be installed.
-	Select the install location and click Install.
-	Installation completed.
Methodology used to scan:
	Intense scan is used. It is a very detailed, comprehensive scan. It is used to get accurate results. The command used is nmap –T4 –A –v scanme.nmap.org. This scan does the following scans and detections to reach the most accurate results as possible:
-	OS detection
-	Version detection
-	Script scanning
-	Traceroute

1.	Nmap scan types:
There are several different Nmap scans which one can utilise to identify open ports on target devices. The more popular scan types are described here. It is always a good idea to know that other scan types exist and how they can be used to circumvent security measures such as Intrusion Detection Systems (IDSs) or help identify ports that regular scans would not pick up.

a.	TCP SYN (Stealth) scan -sS
The TCP SYN scan is the most popular scan. It is semi-stealthy, in that it does not complete the full TCP handshake and extremely fast allowing you to scan thousands of ports per second. To run a TCP SYN scan use the -sS switch as per the example below where we are running a scan on the top 1,000 TCP ports.
nmap -sS –top-ports 1000 <Target IP>

b.	TCP connect scan -sT
The TCP Connect scan makes a full TCP connection to the target i.e. it completes the TCP three-way handshake. As this is a full connection, it is not as stealthy as the SYN scan and is only used if the TCP SYN scan is not an option or is not returning any results. A TCP connect scan uses the -sT switch as shown below where we are running a scan on the top 1,000 TCP ports as we did for the SYN scan.
nmap -sT –top-ports 1000 <Target IP>

c.	UDP scan – sU
Although many services run on the TCP protocol, one must not neglect to scan for open UDP ports on target devices to ensure you obtain as much information about the target as possible. Services such as DNS, DHCP and even VPN’s run on UDP so scanning for open UDP ports is an important step during the reconnaissance phase. The nmap switch for a UDP scan is -sU and below is an example of the nmap syntax to run a UDP scan on the top 1,000 ports.
nmap -sU –top-ports 1000 <Target IP>

d.	NULL (-sN), FIN(-sF) and Xmas(-sX) Scans
NULL, FIN and Xmas Scans take advantage of specifications stated in the TCP RFC. In essence, when scanning targets with a SYN, RST or ACK bit set on the packet, a compliant TCP system will return a RST if the port is closed and nothing id the port is open. Below are examples of the nmap syntax for these scan types for the top 1,000 ports.
NULL = nmap -sN –top-ports 1000 <Target IP>
FIN = nmap -sF –top-ports 1000 <Target IP>
Xmas = nmap -sX –top-ports 1000 <Target IP>

2.	Open & Close ports, and Application running on targeted website:
By default, Nmap scans the most common 1,000 ports for each protocol. As shown below in the screenshot of Zenmap port scan of given target http://scanme.nmap.org/, the number of ports are as :
a.)	Closed ports – 993
b.)	Open ports – 4                                ……….. (for details, please refer screenshots below)
c.)	Filtered ports – 3                           ……….. (for details, please refer screenshots below)


 


 


Exercise 2: 
The most critical step in assessing any network is to probe the network for vulnerabilities. This means using various utilities to scan the network for vulnerabilities. The hackers or intruders uses probing tools to intrude any target network. If a network administrator want to know how vulnerable his network is, it is smart enough to try the same tools that an intruder / hacker would use. There are essentially three type of probes that are usually done. These are:
-	Port scanning: 
This is a process of scanning the well-known ports (there are 1024) or even all the ports (there are 65,535) and seeing which ports are open. Knowing what ports are open, tells a lot about a system. If ports 160 and 161 are open, that tells you that the system is using SNMP (Simple Network Management Protocol). From the perspective of a network administrator, there should be no ports open that are not necessary.

-	Enumerating: 
This is a process whereby the attacker tries to find out what is on the target network. Items such as user accounts, shared folders, printers, and so on are sought after. Any of these might provide a point of attack info to the network administrator.


-	Vulnerability assessment:
This is the use of some tool to seek out known vulnerabilities, or the attacker might try to manually assess vulnerabilities. Some outstanding tools are available for vulnerability assessment. 

-	Apart from these, the network administrator should audit policies, check the firewall logs and check patches.


Exercise 3: 

TOR:
Tor is an internet browser which transfers the activities of a user through a secure channel and makes the browsing history anonymous for ISP. It gives you the access to internet freedom which normally a user doesn’t have it.

IPredator: 
IPredator is a VPN (virtual private networking) service offered with the stated goal of providing internet privacy. A VPN is a network of servers that protects one’s privacy by encrypting the messages and hiding IP address. The VPN provider controls both the VPN software on computer, and the servers in their network.

Differences between TOR & IPredator:
1.	Tor Onion Routing vs. VPN Encryption:

Tor uses Onion Routing, a more complex approach. Onion Routing requires the message to pass through at least three, randomly-selected Tor servers before it gets sent to its final destination. Before the message leaves the computer, the Tor software encrypts the message multiple times. The effect is to give the message layers of encryption that must be peeled, similar to layers of an onion. As the message passes through the network, each server decrypts one of the layers. When the final server in the path peels away the final layer of encryption, it exposes the original message, and forwards it to its destination outside the Tor network. As a result of the encryption and the way Tor servers pass messages between each other, none of the three servers can know both who sent the message, and what the message says. This makes one’s anonymous within the network. To further protect against bad actors trying to hack the network, the Tor software in the computer chooses new server to use approximately every 10 minutes.

When a message is processed with a VPN, the message gets encrypted on the computer and sent to a specific server in the VPN network. There, it is decrypted and forwarded to the final destination. Messages coming to the computer get sent to the VPN server. There they are encrypted and sent to the computer. The VPN software on the computer decrypts the message. Once a VPN connection is established, the same server is used continuously for the duration.





2.	Complete anonymity:

Tor makes it impossible for third parties to trace your online activity. 

While this is nearly true for VPNs, it isn’t always. Additionally, unlike Tor, VPNs can fail and expose your IP address.

3.	Price:

Tor is free to use.
Safe VPN services are paid ones.

Attack that potentially could de-anonymize users in the TOR system:
               	
The attacks aimed at de-anonymising users in the TOR system are Plug-in based attacks, P2P information leakage, Torben attack, Induced Tor guard selection, Raptor routing attack, Unpopular ports exploitation and Low-resource attacks. Among these, P2P information leakage is described below:

P2P Information leakage:
  			This kind of attack is perpetrated in order to de-anonymize Tor users by exploiting their connections to peer-to-peer systems. Indeed, considering for instance the BitTorrent protocol, it is possible for a malicious attacker to retrieve the IP address of a user connecting over TOR to communicate with the torrent tracker. A torrent tracker is a network service the user has to communicate to retrieve information about the list of peers able to share the requested resource. Peers information are provided as couples of IP address and listening port. The attacker exploits in this case the fact that, although the list of trackers may be retrieved anonymously via TOR, P2P connections are often accomplished unsafely, by directly communicating with the peer. Therefore, it is possible for the attacker to exploit the man-in-the-middle (MiTM attack) addiction of the TOR network to alter the content of the list returned by the torrent tracker, by including into the list the IP address of a malicious torrent peer. Since communication with such peer would not be established through TOR, it is possible for the attacker to retrieve the IP address of the user originating the request to the tracker.

Attack that potentially could de-anonymize users in VPN hoster IPredator system:

VPN users are vulnerable to an attack called Website traffic fingerprinting. Very briefly, it's a passive eavesdropping attack, although the adversary only watches encrypted traffic from the VPN, the adversary can still guess what website is being visited, because all websites have specific traffic patterns. The content of the transmission is still hidden, but to which website one connects to, isn't secret anymore. Once the premise is accepted, that VPN's can leak which website one is visiting with a high accuracy, it's not difficult to imagine, that also encrypted Tor traffic hidden by a VPN's could be classified.


