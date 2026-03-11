Practical 1: Packet Tracer - Configure Cisco Routers for OSPF MD5 authentication, NTP and Syslog server.


 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/1 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
R3 	G0/1 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
PC-A 	NIC 	192.168.1.5 	255.255.255.0 	192.168.1.1 
PC-B 	NIC 	192.168.1.6 	255.255.255.0 	192.168.1.1 
PC-C 	NIC 	192.168.3.5 	255.255.255.0 	192.168.3.1 
 
Part 1:OSPF MD5 Authentication. 
Step 1: Test connectivity. All devices should be able to ping all other IP addresses. 
Step 2: Configure OSPF MD5 authentication for all the routers in area 0. 
R1(config)# router ospf 1 
R1(config-router)# area 0 authentication message-digest 
R2(config)# router ospf 1 
R2(config-router)# area 0 authentication message-digest 
R3(config)# router ospf 1 
R3(config-router)# area 0 authentication message-digest 
 
Step 3: Configure the MD5 key for all the routers in area 0. 
R1(config)# interface s0/0/0 
R1(config-if)# ip ospf message-digest-key 1 md5 MD5pa55 
R2(config)# interface s0/0/0 
R2(config-if)# ip ospf message-digest-key 1 md5 MD5pa55 
R2(config-if)# interface s0/0/1 
R2(config-if)# ip ospf message-digest-key 1 md5 MD5pa55 
R3(config)# interface s0/0/1 
R3(config-if)# ip ospf message-digest-key 1 md5 MD5pa55 
Step 4: Verify configurations.  
                  show ip ospf interface. 
Part 2: Configure NTP 
Step 1: Enable NTP authentication on PC-A. 
a.	On PC-A, click NTP under the Services tab to verify NTP service is enabled. 
b.	To configure NTP authentication, click Enable under Authentication. Use key 1 and password NTPpa55 for authentication. 
  Step 2: Configure R1, R2, and R3 as NTP clients. 
R1(config)# ntp server 192.168.1.5 
R2(config)# ntp server 192.168.1.5 R3(config)# ntp server 192.168.1.5 
show ntp status. 
Step 3: Configure routers to update hardware clock. 
R1(config)# ntp update-calendar 
R2(config)# ntp update-calendar 
R3(config)# ntp update-calendar show clock. 
Step 4: Configure NTP authentication on the routers. 
authentication on R1, R2, and R3 using key 1 and password NTPpa55. 
R1(config)# ntp authenticate 
R1(config)# ntp trusted-key 1 
R1(config)# ntp authentication-key 1 md5 NTPpa55  
R2(config)# ntp authenticate  
R2(config)# ntp trusted-key 1 
R2(config)# ntp authentication-key 1 md5 NTPpa55  
R3(config)# ntp authenticate 
 R3(config)# ntp trusted-key 1 
R3(config)# ntp authentication-key 1 md5 NTPpa55 
Step 5: Configure routers to timestamp log messages. 
R1(config)# service timestamps log datetime msec 
R2(config)# service timestamps log datetime msec 
R3(config)# service timestamps log datetime msec 
Part 3: Configure Routers to Log Messages to the Syslog Server. 
Step 1: Configure the routers to identify the remote host (Syslog Server) that will receive logging messages. 
R1(config)# logging host 192.168.1.6 
R2(config)# logging host 192.168.1.6 
            R3(config)# logging host 192.168.1.6 
Step 2: Verify logging configuration.             show logging 
Step 3: Examine logs of the Syslog Server Part 4: Configure R3 to Support SSH Connections. 
Step 1: Configure a domain name. 
R3(config)# ip domain-name ccnasecurity.com 
Step 2: Configure users for login to the SSH server on R3. 
R3(config)# username SSHadmin privilege 15 secret ciscosshpa55 
Step 3: Configure the incoming vty lines on R3. 
R3(config)# line vty 0 4 
R3(config-line)# login local 
R3(config-line)# transport input ssh 
Step 4: Erase existing key pairs on R3. 
R3(config)# crypto key zeroize rsa 
Step 5: Generate the RSA encryption key pair for R3. 
R3(config)# crypto key generate rsa 
How many bits in the modulus [512]: 1024 
Step 6: Verify the SSH configuration. 
show ip ssh 
Step 7: Configure SSH timeouts and authentication parameters. 
R3(config)# ip ssh time-out 90 
R3(config)# ip ssh authentication-retries 2 
R3(config)# ip ssh version 2 
show ip ssh 
Step 8: Attempt to connect to R3 via Telnet from PC-C. 
Open the Desktop of PC-C. Select the Command Prompt icon. From PC-C, enter the command to connect to R3 via Telnet. 
PC> telnet 192.168.3.1 
Step 9: Connect to R3 using SSH on PC-C. 
Open the Desktop of PC-C. Select the Command Prompt icon. From PC-C, enter the command to connect to R3 via SSH. 
PC> ssh –l SSHadmin 192.168.3.1 
Step 10: Connect to R3 using SSH on R2. 
To troubleshoot and maintain R3, the administrator at the ISP must use SSH to access the router CLI. From the CLI of R2, enter the command to connect to R3 via SSH version 2 using the SSHadmin user account. 
R2# ssh –v 2 –l SSHadmin 10.2.2.1 
Step 11: Check result. 
 


	 
Practical 2: Packet Tracer - Configure AAA Authentication on Cisco Routers  



 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/1 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
	G0/0 	192.168.2.1 	255.255.255.252 	N/A 
R3 	G0/1 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
TACACS+ Server 	NIC 	192.168.2.2 	255.255.255.0 	192.168.2.1 
RADIUS Server 	NIC 	192.168.3.2 	255.255.255.0 	192.168.3.1 
PC-A 	NIC 	192.168.1.3 	255.255.255.0 	192.168.1.1 
PC-B 	NIC 	192.168.2.3 	255.255.255.0 	192.168.2.1 
PC-C 	NIC 	192.168.3.3 	255.255.255.0 	192.168.3.1 
 
Part 1: Configure Local AAA Authentication for Console Access on R1 
Step 1: Test connectivity. 
•	Ping from PC-A to PC-B.  
•	Ping from PC-A to PC-C. 
•	Ping from PC-B to PC-C. 
Step 2: Configure a local username on R1. 
R1(config)# username Admin1 secret admin1pa55 
  
 Step 3: Configure local AAA authentication for console access on R1. 
R1(config)# aaa new-model 
R1(config)# aaa authentication login default local 
Step 4: Configure the line console to use the defined AAA authentication method. 
R1(config)# line console 0 
R1(config-line)# login authentication default 
Step 5: Verify the AAA authentication method. 
R1(config-line)# end 
R1# exit 
Username: Admin1 
Password: admin1pa55 
Part 2: Configure Local AAA Authentication for vty Lines on R1 
Step 1: Configure domain name and crypto key for use with SSH.  
         R1(config)# ip domain-name ccnasecurity.com  
         R1(config)# crypto key generate rsa 
How many bits in the modulus [512]: 1024 
Step 2: Configure a named list AAA authentication method for the vty lines on R1. 
R1(config)# aaa authentication login SSH-LOGIN local 
Step 3: Configure the vty lines to use the defined AAA authentication method. 
R1(config)# line vty 0 4 
R1(config-line)# login authentication SSH-LOGIN 
R1(config-line)# transport input ssh 
R1(config-line)# end 
Step 4: Verify the AAA authentication method. 
Verify the SSH configuration SSH to R1 from the command prompt of PC-A. 
. 
PC> ssh –l Admin1 192.168.1.1 
Open 
Password: admin1pa55 
Part 3: Configure Server-Based AAA Authentication Using TACACS+ on R2  
Step 1: Configure a backup local database entry called Admin. 
R2(config)# username Admin2 secret admin2pa55 
Step 2: Verify the TACACS+ Server configuration. 
Step 3: Configure the TACACS+ server specifics on R2. 
R2(config)# tacacs-server host 192.168.2.2 
R2(config)# tacacs-server key tacacspa55 
Step 4: Configure AAA login authentication for console access on R2. 
R2(config)# aaa new-model 
R2(config)# aaa authentication login default group tacacs+ local 
Step 5: Configure the line console to use the defined AAA authentication method. 
R2(config)# line console 0 
R2(config-line)# login authentication default 
Step 6: Verify the AAA authentication method. 
R2(config-line)# end 
R2# exit 
Username: Admin2 
              Password: admin2pa55 
Part 4: Configure Server-Based AAA Authentication Using RADIUS on R3 
   Step 1: Configure a backup local database entry called Admin. 
R3(config)# username Admin3 secret admin3pa55 
Step 2: Verify the RADIUS Server configuration. 
Step 3: Configure the RADIUS server specifics on R3. 
R3(config)# radius-server host 192.168.3.2 
R3(config)# radius-server key radiuspa55 
Step 4: Configure AAA login authentication for console access on R3. 
R3(config)# aaa new-model 
R3(config)# aaa authentication login default group radius local 
Step 5: Configure the line console to use the defined AAA authentication method. 
R3(config)# line console 0 
R3(config-line)# login authentication default 
Step 6: Verify the AAA authentication method. 
R3(config-line)# end 
R3# exit 
Username: Admin3 
Password: admin3pa55 
Step 7: Check results. 
 



	  
Practical 3: Configuring Extended ACLs  


 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interface 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/0 	172.22.34.65 	255.255.255.224 	N/A 
	G0/1 	172.22.34.97 	255.255.255.240 	N/A 
	G0/2 	172.22.34.1 	255.255.255.192 	N/A 
Server 	NIC 	172.22.34.62 	255.255.255.192 	172.22.34.1 
PC1 	NIC 	172.22.34.66 	255.255.255.224 	172.22.34.65 
PC2 	NIC 	172.22.34.98 	255.255.255.240 	172.22.34.97 
 
 
Part 1: Configure, Apply and Verify an Extended Numbered ACL Step 1: Configure an ACL to permit FTP and ICMP. 
a.	From global configuration mode on R1, enter the following command to determine the first valid number for an extended access list. 
R1(config)# access-list ? 
b.	Add 100 to the command, followed by a question mark. 
R1(config)# access-list 100 ? 
c.	To permit FTP traffic, enter permit, followed by a question mark. 
R1(config)# access-list 100 permit ? 
d.	This ACL permits FTP and ICMP. ICMP is listed above, but FTP is not, because FTP uses TCP. Therefore, enter tcp to further refine the ACL help. 
R1(config)# access-list 100 permit tcp ? 
e.	Notice that we could filter just for PC1 by using the host keyword or we could allow any host. In this case, any device is allowed that has an address belonging to the 172.22.34.64/27 network. Enter the network address, followed by a question mark. 
R1(config)# access-list 100 permit tcp 172.22.34.64 ? 
f.	Calculate the wildcard mask determining the binary opposite of a subnet mask. 
11111111.11111111.11111111.11100000 = 255.255.255.224 
00000000.00000000.00000000.00011111 = 0.0.0.31 
g.	Enter the wildcard mask, followed by a question mark. 
R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 ? 
h.	Configure the destination address. In this scenario, we are filtering traffic for a single destination, which is the server. Enter the host keyword followed by the server’s IP address. 
R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 ? 
i.	Notice that one of the options is <cr> (carriage return). In other words, you can press Enter and the statement would permit all TCP traffic. However, we are only permitting FTP traffic; therefore, enter the eq keyword, followed by a question mark to display the available options. Then, enter ftp and press Enter. 
R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ? 
R1(config)# access-list 100 permit tcp 172.22.34.64 
0.0.0.31 host 172.22.34.62 eq ftp 
j.	Create a second access list statement to permit ICMP (ping, etc.) traffic from PC1 to Server. Note that the access list number remains the same and no particular type of ICMP traffic needs to be specified. 
R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62 
k.	All other traffic is denied, by default. 
Step 2: Apply the ACL on the correct interface to filter traffic. 
R1(config)# interface gigabitEthernet 0/0 
R1(config-if)# ip access-group 100 in 
Step 3: Verify the ACL implementation 
a.	Ping from PC1 to Server. If the pings are unsuccessful, verify the IP addresses before continuing. 
b.	FTP from PC1 to Server. The username and password are both cisco.  
PC> ftp 172.22.34.62 
c.	Exit the FTP service of the Server.  
ftp> quit 
d.	Ping from PC1 to PC2. The destination host should be unreachable, because the traffic was not explicitly permitted. 
 
 	 
Part 2 : Configure, Apply and Verify an Extended Named ACL Step 1: Configure an ACL to permit HTTP access and ICMP. 
a.	Named ACLs start with the ip keyword. From global configuration mode of R1, enter the following command, followed by a question mark. 
R1(config)# ip access-list ? 
b.	You can configure named standard and extended ACLs. This access list filters both source and destination IP addresses; therefore, it must be extended. Enter HTTP_ONLY as the name. (For Packet Tracer scoring, the name is case-
sensitive.) 
R1(config)# ip access-list extended HTTP_ONLY 
c.	The prompt changes. You are now in extended named ACL configuration mode. All devices on the PC2 LAN need TCP access. Enter the network address, followed by a question mark. 
R1(config-ext-nacl)# permit tcp 172.22.34.96 ? 
d.	An alternative way to calculate a wildcard is to subtract the subnet mask from 255.255.255.255. 
R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15 ? 
e.	Finish the statement by specifying the server address as you did in Part 1 and filtering www traffic. 
R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www 
f.	Create a second access list statement to permit ICMP (ping, etc.) traffic from PC2 to Server. Note: The prompt remains the same and a specific type of ICMP traffic does not need to be specified. 
R1(config-ext-nacl)# permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62 
g.	All other traffic is denied, by default. Exit out of extended named ACL configuration mode. 
Step 2: Apply the ACL on the correct interface to filter traffic. 
R1(config)# interface gigabitEthernet 0/1 
R1(config-if)# ip access-group HTTP_ONLY in 
Step 3: Verify the ACL implementation. 
a.	Ping from PC2 to Server. The ping should be successful, if the ping is unsuccessful, verify the IP addresses before continuing. 
b.	FTP from PC2 to Server. The connection should fail. 
c.	Open the web browser on PC2 and enter the IP address of Server as the URL. 
The connection should be successful. 
  
 


	 
Practical 4: Configuring IP ACLs to Mitigate Attacks.  



 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/1 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
	Lo0 	192.168.2.1 	255.255.255.0 	N/A 
R3 	G0/1 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
PC-A 	NIC 	192.168.1.3 	255.255.255.0 	192.168.1.1 
PC-C 	NIC 	192.168.3.3 	255.255.255.0 	192.168.3.1 
 
Part 1: Verify Basic Network Connectivity 
Verify network connectivity prior to configuring the IP ACLs. 
Step 1: From PC-A, verify connectivity to PC-C and R2. 
a.	From the command prompt, ping PC-C (192.168.3.3). 
b.	From the command prompt, establish an SSH session to R2 Lo0 interface (192.168.2.1) using username SSHadmin and password ciscosshpa55. Close the SSH session when finished.  
PC> ssh -l SSHadmin 192.168.2.1 
c.	Open a web browser to the PC-A server (192.168.1.3) to display the web page. Close the browser when done. 
Part 2: Secure Access to Routers 
Step 1: Configure ACL 10 to block all remote access to the routers except from PC-C. 
Use the access-list command to create a numbered IP ACL on R1, R2, and R3. 
R1(config)# access-list 10 permit host 192.168.3.3 
R2(config)# access-list 10 permit host 192.168.3.3 
R3(config)# access-list 10 permit host 192.168.3.3 
Step 2: Apply ACL 10 to ingress traffic on the VTY lines. 
Use the access-class command to apply the access list to incoming traffic on the VTY lines. 
R1(config-line)# access-class 10 in 
R2(config-line)# access-class 10 in 
R3(config-line)# access-class 10 in 
Step 3: Verify exclusive access from management station PC-C. 
a.	Establish an SSH session to 192.168.2.1 from PC-C (should be successful). 
PC> ssh –l SSHadmin 192.168.2.1 
b.	Establish an SSH session to 192.168.2.1 from PC-A (should fail). 
Part 3: Create a Numbered IP ACL 120 on R1 
Create an IP ACL numbered 120 with the following rules: 
•	Permit any outside host to access DNS, SMTP, and FTP services on server PC-A. 
•	Deny any outside host access to HTTPS services on PC-A. 
•	Permit PC-C to access R1 via SSH. 
Note: Check Results will not show a correct configuration for ACL 120 until you modify it in Part 4. 
Step 1: Verify that PC-C can access the PC-A via HTTPS using the web browser. 
Be sure to disable HTTP and enable HTTPS on server PC-A. 
  Step 2: Configure ACL 120 to specifically permit and deny the specified traffic. 
Use the access-list command to create a numbered IP ACL. 
R1(config)# access-list 120 permit udp any host 192.168.1.3 eq domain 
R1(config)# access-list 120 permit tcp any host 192.168.1.3 eq smtp 
R1(config)# access-list 120 permit tcp any host 192.168.1.3 eq ftp 
R1(config)# access-list 120 deny tcp any host 192.168.1.3 eq 443 
R1(config)# access-list 120 permit tcp host 192.168.3.3 host 10.1.1.1 eq 22 
Step 3: Apply the ACL to interface S0/0/0. 
Use the ip access-group command to apply the access list to incoming traffic on interface S0/0/0. 
R1(config)# interface s0/0/0 
R1(config-if)# ip access-group 120 in 
Step 4: Verify that PC-C cannot access PC-A via HTTPS using the web browser. 
Part 4: Modify an Existing ACL on R1 
Permit ICMP echo replies and destination unreachable messages from the outside network (relative to R1). Deny all other incoming ICMP packets. 
Step 1: Verify that PC-A cannot successfully ping the loopback interface on R2. 
Step 2: Make any necessary changes to ACL 120 to permit and deny the specified traffic. 
Use the access-list command to create a numbered IP ACL. 
R1(config)# access-list 120 permit icmp any any echo-reply 
R1(config)# access-list 120 permit icmp any any unreachable 
R1(config)# access-list 120 deny icmp any any 
R1(config)# access-list 120 permit ip any any 
Step 3: Verify that PC-A can successfully ping the loopback interface on R2. 
Part 5: Create a Numbered IP ACL 110 on R3 
Deny all outbound packets with source address outside the range of internal IP addresses on R3. 
Step 1: Configure ACL 110 to permit only traffic from the inside network. 
Use the access-list command to create a numbered IP ACL. R3(config)# access-list 110 permit ip 192.168.3.0 0.0.0.255 any 
Step 2: Apply the ACL to interface G0/1. 
Use the ip access-group command to apply the access list to incoming traffic on interface G0/1. 
R3(config)# interface g0/1 
R3(config-if)# ip access-group 110 in 
Part 6: Create a Numbered IP ACL 100 on R3 
On R3, block all packets containing the source IP address from the following pool of addresses: any RFC 1918 private addresses, 127.0.0.0/8, and any IP multicast address. Since PC-C is being used for remote administration, permit SSH traffic from the 10.0.0.0/8 network to return to the host PC-C. 
You should also block traffic sourced from your own internal address space if it is not an RFC 1918 address. In this activity, your internal address space is part of the private address space specified in RFC 1918. Use the access-list command to create a numbered IP ACL. 
R3(config)# access-list 100 permit tcp 10.0.0.0 0.255.255.255 eq 22 host 192.168.3.3 
R3(config)# access-list 100 deny ip 10.0.0.0 0.255.255.255 any 
R3(config)# access-list 100 deny ip 172.16.0.0 0.15.255.255 any 
R3(config)# access-list 100 deny ip 192.168.0.0 0.0.255.255 any 
R3(config)# access-list 100 deny ip 127.0.0.0 0.255.255.255 any 
R3(config)# access-list 100 deny ip 224.0.0.0 15.255.255.255 any 
R3(config)# access-list 100 permit ip any any 
Step 2: Apply the ACL to interface Serial 0/0/1. 
Use the ip access-group command to apply the access list to incoming traffic on interface Serial 0/0/1. 
R3(config)# interface s0/0/1 
R3(config-if)# ip access-group 100 in 
Step 3: Confirm that the specified traffic entering interface Serial 0/0/1 is handled correctly. 
a.	From the PC-C command prompt, ping the PC-A server. The ICMP echo replies are blocked by the ACL since they are sourced from the 192.168.0.0/16 address space. 
b.	Establish an SSH session to 192.168.2.1 from PC-C (should be successful). 
 
 	 
PART4: Configuring IPv6 ACLs 
  
Device name 	interface 	Default Gateway 
R1 	➔g0/0 2001:db8:1:1::1/64 ? 
➔ 
s0/0/0 2001:db8:1:a001::1/64 eui-64 	 
R2 	➔ 
s0/0/0 	2001:db8:1:a001::2/64 eui-64 	 
	➔ 
s0/0/1 	2001:db8:1:a002::1/64 eui-64 	
	➔ 
g0/1 	2001:db8:1:2::1/64 eui-64 	
R3 	➔ 
s0/0/1 	2001:db8:1:a002::2/64 eui-64 	 
	➔ 
G0/0 	2001:db8:1:3::1/64 eui-64 	
Server3 	2001:DB8:1:30::30/64 	FE80::30 
 
R1: 
Router>en 
Router#conf t 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 unicast-routing 
Router(config)#int g0/0 
Router(config-if)#ipv6 address 2001:db8:1:1::1/64 ? anycast Configure as an anycast eui-64 Use eui-64 interface identifier 
<cr> 
Router(config-if)#ipv6 address 2001:db8:1:1::1/64 eui-64 
Router(config-if)#ipv6 enable 
Router(config-if)#no shut 
Router(config-if)# 
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up  
Router(config-if)#ex 
Router(config)#int s0/0/0 
Router(config-if)#ipv6 address 2001:db8:1:a001::1/64 eui-64 
Router(config-if)#ipv6 enable Router(config-if)#no shut 
%LINK-5-CHANGED: Interface Serial0/0/0, changed state to down 
Router(config-if)# 
Router(config-if)# 
%LINK-5-CHANGED: Interface Serial0/0/0, changed state to up 
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/0, changed state to up 
R2: 
Router>en 
Router#conf t 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 unicast-routing 
Router(config)#int s0/0/0 
Router(config-if)#ipv6 address 2001:db8:1:a001::2/64 eui-64 
Router(config-if)#ipv6 enable Router(config-if)#no shut 
Router(config-if)# 
%LINK-5-CHANGED: Interface Serial0/0/0, changed state to up 
Router(config-if)# 
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/0, changed state to up 
Router(config-if)#EX 
Router(config)#int s0/0/1 
Router(config-if)#ipv6 address 2001:db8:1:a002::1/64 eui-64 
Router(config-if)#ipv6 enable 
Router(config-if)#no shut 
%LINK-5-CHANGED: Interface Serial0/0/1, changed state to down 
Router(config-if)#int g0/1 
Router(config-if)#ipv6 address 2001:db8:1:2::1/64 eui-64 
Router(config-if)#ipv6 enable Router(config-if)#no shut 
Router(config-if)# 
%LINK-5-CHANGED: Interface GigabitEthernet0/1, changed state to up 
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to up 
%LINK-5-CHANGED: Interface Serial0/0/1, changed state to up %LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/1, changed state to up R3: 
Router>EN 
Router#CONF T 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 unicast-routing 
Router(config)#int s0/0/1 
Router(config-if)#ipv6 address 2001:db8:1:a002::2/64 eui-64 
Router(config-if)#ipv6 enable Router(config-if)#no shut 
Router(config-if)# 
%LINK-5-CHANGED: Interface Serial0/0/1, changed state to up 
Router(config-if)# 
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/1, changed state to up 
Router(config-if)#int G0/0 
Router(config-if)#ipv6 address 2001:db8:1:3::1/64 eui-64 
Router(config-if)#ipv6 enable Router(config-if)#no shut 
Router(config-if)# 
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to up 
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed 
state to up R1: 
Router>EN 
Router#CONF T 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 unicast-routing 
Router(config)#ipv6 route ::/0 2001:db8:1:a001::2 
Router(config)#ipv6 unicast-routing 
Router(config)#ipv6 route 2001:db8:1:2::/64 2001:db8:1:a001::2 Router(config)#ipv6 route 2001:db8:1:3::/64 2001:db8:1:a001::2  Router(config)#ipv6 route 2001:db8:1:a002::/64 2001:db8:1:a001::2 
R2: 
Router>en 
Router#conf t 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)# 
Router(config)#ipv6 route 2001:db8:1:1::/64 s0/0/0 
Router(config)#ipv6 route 2001:db8:1:3::/64 s0/0/1 2001:db8:1:a002::2 Router(config)#ex 
 
R3: 
Router>en 
Router#conf t 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 unicast-routing 
Router(config)#ipv6 route ::/0 2001:db8:1:a002::1  
Router(config)#ex  
R1: 
Router>en 
Router#conf t 
Enter configuration commands, one per line. End with CNTL/Z. 
Router(config)#ipv6 access-list ? 
WORD User selected string identifying this access list  
Router(config)#ipv6 access-list RESTRICTED-LAN 
Router(config-ipv6-acl)#deny ? icmp Internet Control Message Protocol ipv6 Any IPv6 tcp Transmission Control Protocol udp User Datagram Protocol Router(config-ipv6-acl)#deny tcp ? 
X:X:X:X::X/<0-128> IPv6 source prefix x:x::y/<z> any Any source prefix host A single source host 
Router(config-ipv6-acl)#deny tcp any ? 
X:X:X:X::X/<0-128> IPv6 destination prefix x:x::y/<z> any Any destination host eq Match only packets on a given port number gt Match only packets with a greater port number host A single destination host 
lt Match only packets with a lower port number neq Match only packets not on a given port number range Match only packets in the range of port numbers Router(config-ipv6acl)#deny tcp any host ? 
X:X:X:X::X IPv6 destination address x:x::y 
Router(config-ipv6-acl)#deny tcp any host eq ? % 
Unrecognized command 
Router(config-ipv6-acl)#deny tcp any host 2001:db8:1:a002::1 
 
 


 
Practical 5: Configuring a Zone-based policy firewall  


 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/1 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
R3 	G0/1 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
PC-A 	NIC 	192.168.1.3 	255.255.255.0 	192.168.1.1 
PC-C 	NIC 	192.168.3.3 	255.255.255.0 	192.168.3.1 
 
Part 1: Verify Basic Network Connectivity 
Step 1: From the PC-A command prompt, ping PC-C at 192.168.3.3. 
Step 2: Access R2 using SSH. 
a.	From the PC-C command prompt, SSH to the S0/0/1 interface on R2 at 10.2.2.2. 
Use the username Admin and password Adminpa55 to log in.  
PC> ssh -l Admin 10.2.2.2 
b.	Exit the SSH session. 
Step 3: From PC-C, open a web browser to the PC-A server. 
a.	Click the Desktop tab and then click the Web Browser application. Enter the PC-A IP address 192.168.1.3 as the URL. The Packet Tracer welcome page from the web server should be displayed. 
b.	Close the browser on PC-C 
Part 2: Create the Firewall Zones on R3 
Step 1: Enable the Security Technology package. 
a.	On R3, issue the show version command to view the Technology Package license information. 
b.	If the Security Technology package has not been enabled, use the following command to enable the package. 
R3(config)# license boot module c1900 technology-package securityk9 
c.	Accept the end-user license agreement. 
d.	Save the running-config and reload the router to enable the security license. 
e.	Verify that the Security Technology package has been enabled by using the show version command. 
Step 2: Create an internal zone. 
Use the zone security command to create a zone named IN-ZONE. 
R3(config)# zone security IN-ZONE 
R3(config-sec-zone) exit 
Step 3: Create an external zone. 
Use the zone security command to create a zone named OUT-ZONE. 
R3(config-sec-zone)# zone security OUT-ZONE 
R3(config-sec-zone)# exit 
Part 3: Identify Traffic Using a Class-Map 
Step 1: Create an ACL that defines internal traffic. 
Use the access-list command to create extended ACL 101 to permit all IP protocols from the 192.168.3.0/24 source network to any destination. 
R3(config)# access-list 101 permit ip 192.168.3.0 0.0.0.255 any 
Step 2: Create a class map referencing the internal traffic ACL. 
Use the class-map type inspect command with the match-all option to create a class map named IN-NETCLASS-MAP. Use the match access-group command to match ACL 101. 
R3(config)# class-map type inspect match-all IN-NET-CLASS-MAP 
R3(config-cmap)# match access-group 101 
R3(config-cmap)# exit 
Part 4: Specify Firewall Policies 
Step 1: Create a policy map to determine what to do with matched traffic. 
Use the policy-map type inspect command and create a policy map named IN-2-OUTPMAP. 
R3(config)# policy-map type inspect IN-2-OUT-PMAP 
Step 2: Specify a class type of inspect and reference class map IN-NETCLASS-MAP. R3(config-pmap)# class type inspect IN-NET-CLASS-MAP 
Step 3: Specify the action of inspect for this policy map. 
The use of the inspect command invokes context-based access control 
R3(config-pmap-c)# inspect  
All protocols will be inspected. 
R3(config-pmap-c)# exit 
R3(config-pmap)# exit  Part 5: Apply Firewall Policies 
Step 1: Create a pair of zones. 
Using the zone-pair security command, create a zone pair named IN-2-OUT-ZPAIR. Specify the source and destination zones that were created in Task 1. 
 
R3(config)# zone-pair security IN-2-OUT-ZPAIR source IN-ZONE destination 
OUTZONE 
Step 2: Specify the policy map for handling the traffic between the two zones. 
Attach a policy-map and its associated actions to the zone pair using the service-policy type inspect command and reference the policy map previously created, IN-2-OUT-PMAP. 
R3(config-sec-zone-pair)# service-policy type inspect IN-2-OUT-PMAP 
R3(config-sec-zone-pair)# exit 
Step 3: Assign interfaces to the appropriate security zones. 
Use the zone-member security command in interface configuration mode to assign G0/1 to IN-ZONE and S0/0/1 to OUT-ZONE. 
R3(config)# interface g0/1 
R3(config-if)# zone-member security IN-ZONE 
R3(config-if)# exit 
R3(config)# interface s0/0/1 
R3(config-if)# zone-member security OUT-ZONE 
R3(config-if)# exit 
Step 4: Copy the running configuration to the startup configuration. 
Part 6: Test Firewall Functionality from IN-ZONE to OUT-ZONE 
Step 1: From internal PC-C, ping the external PC-A server. 
Step 2: From internal PC-C, SSH to the R2 S0/0/1 interface. 
R3# show policy-map type inspect zone-pair sessions 
Step 3: From PC-C, exit the SSH session on R2 and close the command prompt window. 
Step 4: From internal PC-C, open a web browser to the PC-A server web page. 
R3# show policy-map type inspect zone-pair sessions 
Step 5: Close the browser on PC-C. 
Part 7: Test Firewall Functionality from OUT-ZONE to IN-ZONE  
Step 1: From the PC-A server command prompt, ping PC-C. 
From the PC-A command prompt, ping PC-C at 192.168.3.3. The ping should fail. 
Step 2: From R2, ping PC-C. 
From R2, ping PC-C at 192.168.3.3. The ping should fail. 
 


	 
Practical 6: Configuring IOS Intrusion Prevention System(IPS) using the CLI  


 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/1 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
R3 	G0/1 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
Syslog 	NIC 	192.168.1.50 	255.255.255.0 	192.168.1.1 
PC-A 	NIC 	192.168.1.2 	255.255.255.0 	192.168.1.1 
PC-C 	NIC 	192.168.3.2 	255.255.255.0 	192.168.3.1 
Part 1: Enable IOS IPS 
Step 1: Enable the Security Technology package 
  
R1(config)# license boot module c1900 technology-package securityk9 
 
Step 2: Verify network connectivity. 
a.	Ping from PC-C to PC-A 
b.	Ping from PC-A to PC-C 
Step 3: Create an IOS IPS configuration directory in flash 
Router# mkdir ipsdir 
Step 4: Configure the IPS signature storage location 
R1(config)# ip ips config location flash:ipsdir 
Step 5: Create an IPS rule. 
R1(config)# ip ips name iosips 
Step 6: Enable logging 
R1(config)# ip ips notify log 
R1# clock set 10:20:00 10 january 2014 
R1(config)# service timestamps log datetime msec 
R1(config)# logging host 192.168.1.50 
Step 7: Configure IOS IPS to use the signature categories. 
R1(config)# ip ips signature-category 
R1(config-ips-category)# category all 
R1(config-ips-category-action)# retired true R1(config-ips-category-action)# exit 
R1(config-ips-category)# category ios_ips basic 
R1(config-ips-category-action)# retired false 
R1(config-ips-category-action)# exit 
R1(config-ips-cateogry)# exit 
Step 8: Apply the IPS rule to an interface 
R1(config)# interface g0/1 R1(config-if)# ip ips iosips out 
Part 2: Modify the Signature 
Step 1: Change the event-action of a signature. 
R1(config)# ip ips signature-definition 
R1(config-sigdef)# signature 2004 0  
R1(config-sigdef-sig)# status 
R1(config-sigdef-sig-status)# retired false 
R1(config-sigdef-sig-status)# enabled true 
R1(config-sigdef-sig-status)# exit 
R1(config-sigdef-sig)# engine 
R1(config-sigdef-sig-engine)# event-action produce-alert 
R1(config-sigdef-sig-engine)# event-action deny-packet-inline 
R1(config-sigdef-sig-engine)# exit 
R1(config-sigdef-sig)# exit 
R1(config-sigdef)# exit 
Step 2: Use show commands to verify IPS. 
R1(config)# show ip ips all 
Step 3: Verify that IPS is working properly 
Again, 
Ping PC-A to PC-C 
Ping PC-C to PC-A 
 
Step 4: View the syslog messages 
 
  
 

	  
Practical 7: Packet Tracer Layer 2 Security  



 
TOPOLOGY: 
  
Part 1: Configure Root Bridge 
Step 1: Determine the current root bridge. 
From Central, issue the show spanning-tree command to determine the current root bridge, to see the ports in use, and to see their status. 
Current root is SW-1. 
Step 2: Assign Central as the primary root bridge 
Central(config)# spanning-tree vlan 1 root primary 
Step 3: Assign SW-1 as a secondary root bridge 
SW-1(config)# spanning-tree vlan 1 root secondary. 
Step 4: Verify the spanning-tree configuration 
Central# show spanning-tree LAN0001 
Spanning tree enabled protocol ieee 
 	Root ID Priority 	24577 
 	Address 	00D0.D31C.634C 
This bridge is the 
root 
 	Hello Time 2 sec Max Age 20 sec 	Forward Delay 15 sec 
Part 2: Protect Against STP Attacks 
Step 1: Enable PortFast on all access ports  
             SW-A(config)# interface range f0/1 – 4 
SW-A(config-if-range)# spanning-tree portfast 
SW-B(config)# interface range f0/1 – 4 
SW-B(config-if-range)# spanning-tree portfast  
Step 2: Enable BPDU guard on all access ports. 
SW-A(config)# interface range f0/1 - 4 
SW-A(config-if-range)# spanning-tree bpduguard enable 
SW-B(config)# interface range f0/1 - 4  
SW-B(config-ifrange)# spanning-tree bpduguard enable 
Step 3: Enable root guard 
SW-1(config)# interface range f0/23 - 24  
SW-1(config-if-range)# spanning-tree guard root 
SW-2(config)# interface range f0/23 - 24  SW-2(config-if-range)# spanning-tree guard root 
Part 3: Configure Port Security and Disable Unused Ports 
Step 1: Configure basic port security on all ports connected to host devices. 
SW-A(config)# interface range f0/1 - 22 
SW-A(config-if-range)# switchport mode access 
SW-A(config-if-range)# switchport port-security 
SW-A(config-if-range)# switchport port-security maximum 2 
SW-A(config-if-range)# switchport port-security violation shutdown 
SW-A(config-if-range)# switchport port-security mac-address sticky 
SW-B(config)# interface range f0/1 - 22 
SW-B(config-if-range)# switchport mode access 
SW-B(config-if-range)# switchport port-security 
SW-B(config-if-range)# switchport port-security maximum 2 SW-B(config-if-range)# switchport port-security violation shutdown 
             SW-B(config-if-range)# switchport port-security mac-address sticky 
 
Step 2: Verify port security. 
a. On SW-A, issue the command show port-security interface f0/1 to verify that port 
security has been configured. 
SW-A# show port-security interface f0/1 
Port Security 	: 
Enabled 
 	Port Status 	: Secure-up 
Violation Mode 	: 
Shutdown 
 	Aging Time 	: 0 mins  	Aging Type 	: Absolute 
SecureStatic Address Aging : Disabled 
Maximum MAC Addresses 		: 
2 
	Total MAC Addresses 	: 
0 
Configured MAC Addresses : 
0 
Sticky MAC Addresses 	: 
0 	
Last Source Address:Vlan 	: 0000.0000.0000:0
 	Security Violation Count : 0 
b. Ping from C1 to C2 and issue the command show port-security interface f0/1 again to verify that the switch has learned the MAC address for C1. 
Step 3: Disable unused ports. 
SW-A(config)# interface range f0/5 - 22 
SW-A(config-if-range)# shutdown 
SW-B(config)# interface range f0/5 - 22 
SW-B(config-if-range)shutdown  
Step 4: Check results.




Practical 8: Layer 2 VLAN Security  



 
TOPOLOGY: 
  
ADDRESSING TABLE: 
PART 1: Verify Connectivity 
Step 1: Verify connectivity between C2 (VLAN 10) and C3 (VLAN 10). 
Step 2: Verify connectivity between C2 (VLAN 10) and D1 (VLAN 5). 
Part 2: Create a Redundant Link Between SW-1 and SW-2 Step 1: Connect SW-1 and SW-2. 
Using a crossover cable, connect port F0/23 on SW-1 to port F0/23 on SW-2. 
Step 2: Enable trunking, including all trunk security mechanisms on the link between SW-1 and SW-2. 
SW-1(config)# interface f0/23 
SW-1(config-if)# switchport mode trunk 
SW-1(config-if)# switchport trunk native vlan 15 
SW-1(config-if)# switchport nonegotiate 
SW-1(config-if)# no shutdown 
SW-2(config)# interface f0/23 
SW-2(config-if)# switchport mode trunk 
SW-2(config-if)# switchport trunk native vlan 15 
SW-2(config-if)# switchport nonegotiate 
SW-2(config-if)# no shutdown 
Part 3: Enable VLAN 20 as a Management VLAN 
Step 1: Enable a management VLAN (VLAN 20) on SW-A. 
a.	Enable VLAN 20 on SW-A. 
SW-A(config)# vlan 20 
SW-A(config-vlan)# exit 
b.	Create an interface VLAN 20 and assign an IP address within the 192.168.20.0/24 network. 
SW-A(config)# interface vlan 20 
SW-A(config-if)# ip address 192.168.20.1 255.255.255.0 
Step 2: Enable the same management VLAN on all other switches. 
Create the management VLAN on all switches: SW-B, SW-1, SW-2, and Central  
  SW-B(config)# vlan 20 SW-B(config-vlan)# exit 
SW-1(config)# vlan 20 
SW-1(config-vlan)# exit 
SW-2(config)# vlan 20 
SW-2(config-vlan)# exit 
Central(config)# vlan 20 
Central(config-vlan)# exit 
Create an interface VLAN 20 on all switches and assign an IP address within the 192.168.20.0/24 network. SW-1(config)# interface vlan 20  
SW-1(config-if)# ip address 192.168.20.3 255.255.255.0 
SW-2(config)# interface vlan 20 
SW-2(config-if)# ip address 192.168.20.4 255.255.255.0 
Central(config)# interface vlan 20 
Central(config-if)# ip address 192.168.20.5 255.255.255.0 
Step 3: Connect and configure the management PC. 
Connect the management PC to SW-A port F0/1 and ensure that it is assigned an available IP address within the 192.168.20.0/24 network. 
Step 4: On SW-A, ensure the management PC is part of VLAN 
20 SW-A(config)# interface f0/1 
SW-A(config-if)# switchport access vlan 20 
SW-A(config-if)# no shutdown 
Step 5: Verify connectivity of the management PC to all switches. 
The management PC should be able to ping SW-A, SW-B, SW-1, SW-2, and Central. 
Part 4: Enable the Management PC to Access Router R1 Step 1: Enable a new subinterface on router R1. 
a.	Create subinterface g0/0.3 and set encapsulation to dot1q 20 to account for VLAN 20. 
R1(config)# interface g0/0.3 
R1(config-subif)# encapsulation dot1q 20 
b.	Assign an IP address within the 192.168.20.0/24 network. 
R1(config)# interface g0/0.3 
R1(config-subif)# ip address 192.168.20.100 255.255.255.0 
Step 2: Verify connectivity between the management PC and R1. 
Be sure to configure the default gateway on the management PC to allow for connectivity. 
Step 3: Enable security. 
Create an ACL that allows only the Management PC to access the router 
R1(config)# access-list 101 deny ip any 192.168.20.0 0.0.0.255 
R1(config)# access-list 101 permit ip any any 
R1(config)# access-list 102 permit ip host 192.168.20.50 any Apply the ACL to the proper interface(s). 
R1(config)# interface g0/0.1 
R1(config-subif)# ip access-group 101 in 
R1(config-subif)# interface g0/0.2 
 

	INFORMATION SECURITY 	 
R1(config-subif)# ip access-group 101 in 
R1(config-subif)# line vty 0 4 
R1(config-line)# access-class 102 in 
    Step 4: Verify security. 
PC> ssh -l SSHadmin 192.168.20.100 
Step 5: Check results. 
 
 
	 
Practical 9: Configure and verify a Site-to-Site IPsec VPN Using CLI  



 
TOPOLOGY: 
  
ADDRESSING TABLE: 
Device 	Interfaces 	IP Address 	Subnet Mask 	Default Gateway 
R1 	G0/0 	192.168.1.1 	255.255.255.0 	N/A 
	S0/0/0 	30.1.1.2 	255.255.255.252 	N/A 
R2 	S0/0/0 	30.1.1.1 	255.255.255.252 	N/A 
	S0/0/1 	40.2.2.1 	255.255.255.252 	N/A 
	G0/0 	192.168.2.1 	255.255.255.0 	N/A 
R3 	G0/0 	192.168.3.1 	255.255.255.0 	N/A 
	S0/0/1 	40.2.2.2 	255.255.255.252 	N/A 
PC-A 	NIC 	192.168.1.3 	255.255.255.0 	192.168.1.1 
PC-B 	NIC 	192.168.2.3 	255.255.255.0 	192.168.2.1 
PC-C 	NIC 	192.168.3.3 	255.255.255.0 	192.168.3.1 
Part 1: Configure IPsec Parameters on R1 
Step 1: Test connectivity. 
Ping from PC-A to PC-C. 
Step 2: Enable the Security Technology package. 
R1# show version 
  
R1(config)# license boot module c1900 technology-package securityk9 
R1(config)# do write 
R1(config)# do reload 
R1# show version 
  
Step 3: Identify interesting traffic on R1. 
R1(config)# access-list 110 permit ip 192.168.1.0 0.0.0.255 192.168.3.0 0.0.0.255 
 
Step 4: Configure the IKE Phase 1 ISAKMP policy on R1 
R1(config)# crypto isakmp policy 10 
R1(config-isakmp)# encryption aes 256 
R1(config-isakmp)# authentication pre-share 
R1(config-isakmp)# group 5 
R1(config-isakmp)# exit 
R1(config)# crypto isakmp key vpnpa55 address 10.2.2.2 
 
Step 5: Configure the IKE Phase 2 IPsec policy on R1 
R1(config)# crypto ipsec transform-set VPN-SET esp-aes esp-shahmac 
R1(config)# crypto map VPN-MAP 10 ipsec-isakmp  
R1(configcrypto-map)# description VPN connection to R3  
R1(config-cryptomap)# set peer 10.2.2.2 
R1(config-crypto-map)# set transform-set VPNSET  
R1(config-crypto-map)# match address 110 
R1(config-crypto-map)# exit 
Step 6: Configure the crypto map on the outgoing interface. 
R1(config)# interface s0/0/0 
R1(config-if)# crypto map VPN-MAP 
Part 2: Configure IPsec Parameters on R3 Step 1: Enable the Security Technology package. 
On R3, issue the show version command to verify that the Security Technology package license information has been enabled. 
a. If the Security Technology package has not been enabled, enable the package and reload R3. 
Step 2: Configure router R3 to support a site-to-site VPN with R1. 
R3(config)# access-list 110 permit ip 192.168.3.0 0.0.0.255 192.168.1.0 0.0.0.255 
Step 3: Configure the IKE Phase 1 ISAKMP properties on R3 R3(config)# crypto isakmp policy 10 R3(config-isakmp)# encryption aes 256 
R3(config-isakmp)# authentication preshare 
R3(config-isakmp)# group 5 
R3(config-isakmp)# exit 
R3(config)# crypto isakmp key vpnpa55 address  
Step 4: Configure the IKE Phase 2 IPsec policy on R3. 
R3(config)# crypto ipsec transform-set VPN-SET esp-aes espsha-hmac 
R3(config)# crypto map VPN-MAP 10 ipsec-isakmp 
R3(config-crypto-map)# description VPN connection to R1 
R3(config-crypto-map)# set peer 10.1.1.2 
R3(config-crypto-map)# set transform-set VPN-SET  
R3(config-crypto-map)# match address 110  
R3(config-crypto-map)# exit 
Step 5: Configure the crypto map on the outgoing interface R3(config)# interface s0/0/1 R3(config-if)# crypto map VPN-MAP 
Part 3: Verify the IPsec VPN 
Step 1: Verify the tunnel prior to interesting traffic. 
Issue the show crypto ipsec sa command on R1. Notice that the number of packets encapsulated, encrypted, decapsulated, and decrypted are all set to 0. 
Step 2: Create interesting traffic. 
Ping PC-C from PC-A. 
Step 3: Verify the tunnel after interesting traffic. 
On R1, re-issue the show crypto ipsec sa command. Notice that the number of packets   is more than 0, which indicates that the IPsec VPN tunnel is working. 
Step 4: Create uninteresting traffic. 
Ping PC-B from PC-A. Note: Issuing a ping from router R1 to PC-C or R3 to PC-A is not interesting traffic. 
 
 
 
 
 
 
