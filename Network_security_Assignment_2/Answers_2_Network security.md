Exercise-1:
1.	Step by step process to crack passphrase:
-	Step 1 – Study & Identify Limitation of the Network
In this step, we learn that WEP network suffers from limitations mentioned (as in the answer of Exercise 1.2 below). To exploit these limitation, we decided to perform Brute force attack. In order to perform this attack, we used a tool called aircrack-ng.
-	Step 2 – Get the MAC Address of target router 
In order to get the MAC Address of the wi-fi router, we have used the airport utility available for macOS. The address e8:94:f6:f2:f1:e1 was identified as the routers MAC Address.

-	Step 3 – Generate a packet capture file
In this step, we generate a .pcap file which is nothing but a tcp packet dump of the network. This is done by Wireless Diagnostics utility available on macOS. Wireless Diagnostics sniffs the network on given channel (in our case channel 6) and generates the required pcap file.

 

-	Step 4 – Using aircrack-ng to get the passphrase 
The tool aircrack-ng setups up a Brute force attack on the specified target with the help of captured network tcpdump and the BSSID (MAC Address) obtained in 2nd step. The command outputs the passphrase of the wi-fi router as shown below in the screenshot.

pallavikhadse$ aircrack-ng -b e8:94:f6:f2:f1:e1 to_break.pcap
Reading packets, please wait...
Opening first.pcap
Read 87871 packets.

1 potential targets

Attack will be restarted every 5000 captured ivs.
Starting PTW attack with 22606 ivs.


		                Aircrack-ng 1.5.2 rev 3dab9517


             		[00:00:00] Tested 578 keys (got 22606 IVs)

   KB    depth   byte(vote)
    0    3/  5   81(27648) 6F(27136) F8(27136) A0(26880) 3B(26880) E3(26880) E1(26624) 38(26624) 21(26624) B0(26368) A6(26368) E4(26112) E6(25856) 33(25856) 88(25856) 64(25600) 
    1    4/  7   6B(28672) 4F(28160) ED(27904) FB(27392) B7(27392) 33(26880) 50(26880) B3(26624) 3B(26624) 5C(26624) A7(26624) 94(26368) F1(26368) B0(26368) E2(26112) B2(26112) 
    2    0/  6   79(29952) F2(28928) 98(28416) 94(27648) C7(27648) EB(27392) 87(27136) 95(27136) CD(26880) 56(26880) 46(26880) A5(26880) 3E(26880) 5E(26624) 3F(26624) 03(26624) 
    3    0/  3   64(30464) 80(30208) 20(27904) 7D(27648) 59(27392) 1D(26880) 29(26880) DA(26880) 27(26624) DD(26624) 0C(26368) B3(26368) 9B(26368) EE(26112) B8(26112) 7A(26112) 
    4    0/  1   32(31744) 2B(28928) 03(28672) 4A(28672) 38(28416) C5(28160) D2(28160) AC(28160) 24(27904) 8E(27392) E2(27392) 68(27136) 7A(27136) 7E(26880) FA(26624) 87(26624) 

                     KEY FOUND! [ 6F:6B:79:64:32 ] (ASCII: okyd2 )
					Decrypted correctly: 100%


2.	Weakness of protocol:
-	One of the weaknesses is that WEP network uses only one static key when transmitting any data from a device. This encryption uses a shared key-authentication and transmits the same key with data-packets across the network.
 
-	The said master key if needs to be changed then the same is done by changing it manually on all the connected devices on that network.

-	IV values can be reused:
IV stands for Initialization vector value, it is an arbitrary number which is used with a secret key for data encryption in wi-fi network. This number is used only once in any session. In the standards, there is no mention about changing this value at-all but reusing keys is considered a greatest cryptographic disadvantage in networks & security system.

-	IV length is short:
There are around 16.7 million numbers of possibilities with 24 bit keys which looks huge but on an overcrowded network, this number can be accomplished within few hours.  Its reuse then becomes difficult to be unavoidable. There are ways to avoid this reuse. One is by starting a key and incrementing it by one for each subsequent key. But there is also a loophole where most of the devices reply to the same key value at start and then adopt the same sequence, creating lots of duplicate values for the attackers/ intruders to hack on.

-	Weak keys are susceptible to attack:
Weak initialisation vectors (IVs) like combinations of certain keys value produces less random data for the first few bytes which can help attackers easily discover the keys and hack the WEP network. The developers most often intentionally avoid using Weak IVs but the consequences of reducing the already limited key possibilities further, increases the chances of reusing the keys. Hence, prone for attack.

-	Master keys are used directly:
Master keys should only be utilized to generate other required temporary keys. WEP encryption is defective by using the master keys directly. From a cryptographic point of view, this is not recommended. 

-	Key Management and updating is poor:
Updating or changing keys are not frequently executed due to which any potential attacker tends to collect maximum data packets, to hack WEP network. Even the administration of WEP keys is not well designed and is difficult to carry on large networks.

-	Message integrity checking is ineffective:
The message integrity checking of WEP encryption is weak and ineffective as the hackers are able to change the messages and cipher a new value to match.



3.	Steps to secure WEP network:
Following are some of the measures that can be taken into consideration while securing WEP network:

-	MAC Address filtering:
MAC Address can be whitelisted/blacklisted on the router, thereby applying a filter of use on the actual user of the network.

-	Adding a layer of authentication:
Adding another step of authentication to the process with a more secure password may help. However, if the attacker is savvy enough they can likely bypass this.

-	Upgrade to WPA2 or equivalent wifi routers:
WEP was deprecated in 2004 and has been deemed insecure for a long time. There is no method to make WEP uncrackable, or at least secure. So buying a new router that supports WPA2 is suggested.



Exercise-2:
1.	Tools used to perform the man in the middle attack & Screenshots of the poisoned ARP cache:

o	Description:

-	ARP stands for Address Resolution Protocol. ARP poison routing or ARP spoofing is a technique by means of which an attacker spoofs false ARP messages in a local area network (LAN). This aim at linking the attacker's MAC address with the IP address of another host, machine or server on the network, such as the default gateway. This result in redirecting any traffic meant for the targeted IP address to be sent to the attackers instead, and also allowing the attacker to intercept data frames, modifying the traffic or even blocking communication. Often the attack is used as an opening for other attacks, such as man in the middle attack, or hijacking attack.

-	Man in the middle attack occurs when an attacker secretly place himself in between two communicating systems and tries to intercept and alter the ongoing transfer of information. A pictorial diagram of man in the middle attack is shown below.
 


o	Tools used to perform man in the middle attack are:
-	Cain and Abel tool
This tool is used for Windows password cracking, sniffing Voice Only Internet Protocol (VOIP) and in Man in the middle attacks against Remote Desktop Protocol (RDP). In order to prevent this attack, strong passwords must be used everywhere.

-	SSLstrip tool
SSLstrip tool attacks and seize HTTP traffic, channel links and maps these links to look alike HTTP links. It includes a nifty feature which has a favicon on the unencrypted connection and is replaced with a padlock symbol to make user feel that the connection is secure. Defending against SSLstrip can be achieved by being aware of the possibility of MITM attacks (ARP, proxies / gateway, wireless) and looking for sudden protocol changes in browser bar.
-	Evilgrade tool
Updating the software is one way of keeping the device secure. This tool fakes the upgrade and provides the user with average update. We need to prevent this by performing updates to system or applications only on a trusted network.

-	Ettercap tool
It is one of the tools to perform attack. We have used Ettercap to perform the man in the middle attack. It is the attack made against ARP protocol by placing itself as man in the middle and performing to:
•	infect, delete, replace data in network
•	detect the passwords for HTTP, FTP, etc
•	furnish false SSLstrip HTTPs certificates to the target device, etc.
Ettercap works by putting the network interface into promiscuous mode and by ARP poisoning/spoofing the target machines. Defending Ettercap can be achieved by Locking down network ports and by using Secure switch configuration.
Ettercap supports active and passive dissection of many protocols and provides many features for network and host analysis.
 
Ettercap offers four modes of operation:
1.	IP-based: packets are filtered based on IP source and destination.
2.	MAC-based: packets are filtered based on MAC address, useful for sniffing connections through a gateway.
3.	ARP-based: uses ARP poisoning to sniff on a switched LAN between two hosts (full-duplex).
4.	PublicARP-based: uses ARP poisoning to sniff on a switched LAN from a victim host to all other hosts (half-duplex).



o	The screeshots of poisoned ARP cache:

 

 

 

 


2.	Prevention of man in the middle attack:
Few practices used to prevent Man in the middle attack
-	Ensure that the website visited has HTTPS at the beginning of the url
-	Don’t click on malicious links or emails
-	Before clicking on emails, check the sender of the email
-	If you’re a website admin, you should implement HSTS
-	Remember to not make a purchase or send sensitive data on a public Wi-Fi network
-	Make sure your website doesn’t have any mixed content
-	If your website is using SSL, make sure you have disabled insecure SSL/TLS protocols
-	Ensure to only have enabled TLS 1.1 and TLS 1.2
-	Do not download pirated content
-	Secure your home/work network
-	Make sure proper security tools are installed on the systems

Man in the middle attacks can be prevented by integrating verification techniques for applications alongside effective encryption.
o	As Individual users
It is very important to create awareness among individual users in preventing Man in the middle attacks -
-	To refrain from connecting to public wi-fi that are not password protected.
-	To ensure not to perform any important tasks like financial transactions when connected to public network.
-	It is recommended to log out of any application when not in use.
-	Be conscious to any alerts or warning messages that the website is insecure.

o	As Website operators
-	Website operators can prevent Man in the middle attack by implementing the use of TLS and HTTPS which allots effective encryption and authentication for data being transmitted to protect the website against the attack.
-	It is also advisable to use SSL/TLS to defend every page of the website and not just the page that includes user’s information as there is a great chance of attacker to extract session cookies when user is on a session that is insecure when logged in.  

o	Preventing HTTP interception
-	In order to prevent HTTP interception we need to implement SSL or TLS certificate to activate HTTPS protocol which is a secure version of HTTP. This protocol encrypts the connection between the web browser and the server mitigating attackers attempts and securing the user’s information.

-	There are various SSL certificate that provides different level of protection. TLS certificate is implemented to merge the identity of domain name and the organization the user chooses to use an Organization validated or Extended validated level certificates.

o	Preventing System and Server Configurations from Man in the middle attack
-	Apart from implementing SSL/TLS, We must ensure that the website does not have any page running on HTTP protocol that could help the hackers. We must make sure that all the hyperlinks in the website uses HTTPS protocol.

-	It is very important to check if the configuration of the server is done as per the standards and best practices by implementing protocols and algorithms. For instance, Verifying TLS 1.1 and 1.2 is enabled and SSL2, TLS1 and SSL3 are disabled.
-	We can also use Comodo SecureBox to protect data on malware infected websites. It secures the data from hackers and runs sessions inside virtual containers by keeping the application safe and secure even on infected systems. 
           	
It is very efficient to deny man in the middle attack with distinctive features like,
-	Application Containerization – An operating system based technique that creates a threat resistant tunnel between web client and the web server to ensure the transactions and communications are secure.
-	Anti Memory Scrapping – It restricts Third party applications from accessing the memory of containerized applications.
-	Remote take over protection – It is equipped with screen capture detection technology. It restricts any remote desktop takeover by obstructing any malicious attempts.
-	Keylogger protection- It has a smart technique that works on artificial intelligence known as Keyboard Visualisation Technology. The keyboard filter drivers helps to block any suspicious single keys or even key combination.
-	Instant Virus Removal – Comodo provides a cloud based scan of any application even before the user access it. It helps in stopping or removing any active virus on host device.

-	Anti-sniffing – When a potential malicious connection is being established comodo intercepts to verify if the certificate’s are matching comodo’s trusted root certificate list, to strictly encounter man in the middle attacks. 


Exercise-3:
o	BEAST SSL vulnerability & its prevention:
BEAST SSL stands for Browser Exploit Against SSL/TLS. SSL is the Secure Socket Layer and TLS Transport Layer Security protocols. This attack takes the advantages of the weaknesses in cipher block chaining (CBC) to exploit the SSL protocol. The CBC vulnerabiliy can permit man in the middle attacks against SSL by providing access to attackers to the data passed between the web server and web browser accessing the Server.
SSL is cryptographic protocol that provide authentication and data encryption between different endpoints. It affects the browser that supports T 1.0 and also the earlier protocols. Here, the hacker can decrypt the data that is exchanged between the browser and the server. It is a client side attack that uses man in the middle technique. The hacker tries to inject the packets to TLS stream allowing them to predict Initialization Vector (IV) used with the injected messages and then compare the results to the one of the blocks which they prefer to decrypt. In order to succeed, the hacker must have some control of the targeted client’s browser.
A BEAST attack to take place, following are three stringent conditions that must be met:
-	A vulnerable version of SSL must be in use with a block cipher 
-	The attacker must be actively monitoring the SSL connection by implementing man in the middle attack.
-	There should be possibility to inject an applet or javascript into the same origin of the targeted web site 
This attack can be achieved with Cross-site scripting (XSS) if the vulnerability in a file upload system is known and then can be used. Therefore, if an application is vulnerable to cross-site scripting or has a weak file upload system then the hacker will utilize this vulnerability to achieve his desired impact.
o	Prevention:
We can prevent this attack in web browser by using TLS 1.1 or TLS 1.2 protocols and disable TLS 1.0, disabling this protocol improves the overall security of the SecureAuth IdP Appliance. To mitigate in the operating system   we should ensure that the SecureAuth IdP Appliance is fully patched with the latest Microsoft Windows Server updates.
