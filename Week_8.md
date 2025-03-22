# Week 8.1
## Network Security
Review the three suspicious incidents at Acme Corp. For each, document the client and server and describe the request and response in simple terms. <br>
1. A hacker logs into Microsoft Outlook with the stolen username and password of Acme's CFO. The hacker sends an email to the head of accounting asking them to wire $10,000 to a foreign account owned by the hacker.<br>
**Client:** Microsoft Outlook <br>
**Server:** Outlook Mail server <br>
**Request:** The client sends a login request to the email server and sends an email. <br>
**Response:** The server processes the login request and sends the email. <br>
2. A hacker uses Firefox to visit the administrative website of Acme Corp, where they attempt to log into the CFO's account multiple times until they correctly guess the password.<br>
**Client:** Firefox <br>
**Server:** Web Server <br>
**Request:** Brute force login requests sent to the server. <br>
Response: Server is rejecting the invalid requests until access is granted. <br>
3. A hacker steals the Acme CFO's mobile phone. Login credentials were saved on the phone, allowing the hacker to log into Acme Corp's mobile admin application.<br>
**Client:** Admin Mobile Application<br>
**Server:** Application Server<br>
**Request:** Using the stored credentails the client sends a login request to the server<br>
**Response:** The server accepts the login request and access is granted.<br>

## Network Devices
Design the office with the following computer and network devices: <br>
(6) Employee computers<br>
(2) Switches<br>
(1) Router<br>
(1) Load balancer<br>
(1) Firewall<br>
(1) Representation of the internet<br>
(2) Servers<br>
(1) Wireless access point with (1) firewall to protect it<br>
Create a DMZ.<br>
Use lines to separate the DMZ, LAN, and WAN.<br>
Add the server and load balancer to the DMZ and place the rest of the devices in appropriate locations.<br>

