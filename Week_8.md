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
![image](https://github.com/Tapjelly/Networking-and-Encryption/blob/Images/NetworkDeviceActivity.png)

## Network Addressing
Convert the following binary representations into numeric IP addresses:<br>
Determine whether the numeric IP addresses are public or private.<br>
Compare the numeric IP addresses to the Acme server list and determine to which server the IPs belong.<br>
Summarize your findings to determine what resources the hacker is trying to access.<br><br>
11000000101010000100010110010001 > 192.168.69.145 is Private and our Trade Secrets Server<br>
00001010000000000000000000101010 > 10.0.0.42 is Private and our Trade Secrets Server<br>
11000000101011000100010110010001 > 192.172.69.145 is Public and our Trade Secrets Server<br>
00101001001011011011011000100000 > 41.45.182.32 is Public and our Intellectual Property Secrets Server<br>
00001010000000000000000001001100 > 10.0.0.76 is Private and our Trade Secrets Server<br>
The Attacker is trying to target all of our Trade Secrets.

Convert the following binary: <br>
100010001111011111000111011001010001101000110110 > 88:F7:C7:65:1A:36 is the hackers Mac Address.<br>

## DNS Hijacking
We want to spoof the record for acmetradesecrets.org to be redirected to the IP of address of 45.33.32.156 (scanme.nmap.org).
<br>To do this we will nano into /etc/hosts<br>
Within hosts we will add this line to the bottom of the file and save: <br>
45.33.32.156 acmetradesecrets.org

# Week 8.2
## Internet Protocols
For this activity we were tasked with converting a binary to a readable log and identifying the type. I will inlcude only the readable log in my solution.

Log File 1 =  HTTP
GET / HTTP/1.1
Host: widgets.com
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.117 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,nb;q=0.8

Log File 2 = FTP
File Transfer Protocol (FTP)
    230 Login successful.\r\n
        Response code: User logged in, proceed (230)
        Response arg: Login successful.

Log File 3 = TLSV1.2
TLSv1.2 Record Layer: Application Data Protocol: http-over-tls
    Content Type: Application Data (23)
    Version: TLS 1.2 (0x0303)
    Length: 56
    Encrypted Application Data: d03ff41452da9e9c3ec76cbeb35e8ffc1f64bf80f512924a?

Log File 4 = DNS
Domain Name System (query)
    Transaction ID: 0x18b6
    Flags: 0x0100 Standard query
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data: Unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        applegate.com: type A, class IN
    [Response In: 623]

Log File 5 = ARP
Address Resolution Protocol (request)
    Hardware type: Ethernet (1)
    Protocol type: IPv4 (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (1)
    Sender MAC address: Technico_65:1a:36 (88:f7:c7:65:1a:36)
    Sender IP address: 10.0.0.1
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 10.0.0.6
    
Log File 6 = HCI
HCI H4
    [Direction: Unspecified (0xffffffff)]
    HCI Packet Type: HCI Command (0x01)
HCI Command - Read Local Supported Features
    Command Opcode: Read Local Supported Features (0x1003)
    Parameter Total Length: 0
    [Response in frame: 4]
    [Command-Response Delta: 4.181ms]

## Ports

Here we were given logs and tasked with determining the source and desitnation ports, the protocol associated with each port, and research what the port can be used for.
Log Record 1:

We are using port 80 which is HTTP. This is used for data transmittion in plain text.

Src: 192.168.1.9, Dst: 192.124.249.168
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x00 (DSCP: CS0, ECN: Not-ECT)
    Total Length: 942
    Identification: 0x4103 (16643)
    Flags: 0x4000, Don't fragment
    Time to live: 128
    Protocol: TCP (6)
    Header checksum: 0x3a70 [validation disabled]
    [Header checksum status: Unverified]
    Source: 192.168.1.9
    Destination: 192.124.249.168
Src Port: 50152, Dst Port: 80, Seq: 3879, Ack: 39771, Len: 902
    **Source Port: 50152**
    **Destination Port: 80**
    [Stream index: 82]
    [TCP Segment Len: 902]
    Sequence number: 3879    (relative sequence number)
    [Next sequence number: 4781    (relative sequence number)]
    Acknowledgment number: 39771    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x018 (PSH, ACK)
    Window size value: 256
    [Calculated window size: 65536]

Log Record 2

We are using port 443 which is HTTPS. This is used for data transmittion over a secured network through encryption.


Src: 10.0.0.42, Dst: 35.186.241.40
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x00 (DSCP: CS0, ECN: Not-ECT)
    Total Length: 86
    Identification: 0x0211 (529)
    Flags: 0x4000, Don't fragment
    Time to live: 128
    Protocol: TCP (6)
    Header checksum: 0xd984 [validation disabled]
    [Header checksum status: Unverified]
    Source: 10.0.0.42
    Destination: 35.186.241.40
Src Port: 53367, Dst Port: 443, Seq: 1136, Ack: 1307, Len: 46
    **Source Port: 53367**
    **Destination Port: 443**
    [Stream index: 113]
    [TCP Segment Len: 46]
    Sequence number: 1136    (relative sequence number)
    [Next sequence number: 1182    (relative sequence number)]
    Acknowledgment number: 1307    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x018 (PSH, ACK)
    Window size value: 251
    [Calculated window size: 64256]
    [Window size scaling factor: 256]
    Checksum: 0xc5d7 [unverified]
    [Checksum Status: Unverified]
    Urgent pointer: 0
    [SEQ/ACK analysis]
    [Timestamps]
    TCP payload (46 bytes)

Log Record 3

We are using port 21 which is FTP. This is used for the transmittion of files between server and client.

Src: 192.168.29.54, Dst: 90.130.70.73
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x10 (DSCP: Unknown, ECN: Not-ECT)
    Total Length: 59
    Identification: 0xcccd (52429)
    Flags: 0x4000, Don't fragment
    Time to live: 64
    Protocol: TCP (6)
    Header checksum: 0xef35 [validation disabled]
    [Header checksum status: Unverified]
    Source: 192.168.29.54
    Destination: 90.130.70.73
Src Port: 64836, Dst Port: 21, Seq: 17, Ack: 55, Len: 7
    **Source Port: 64836**
    **Destination Port: 21**
    [Stream index: 2]
    [TCP Segment Len: 7]
    Sequence number: 17    (relative sequence number)
    [Next sequence number: 24    (relative sequence number)]
    Acknowledgment number: 55    (relative ack number)
    1000 .... = Header Length: 32 bytes (8)
    Flags: 0x018 (PSH, ACK)
        000. .... .... = Reserved: Not set
        ...0 .... .... = Nonce: Not set
        .... 0... .... = Congestion Window Reduced (CWR): Not set
        .... .0.. .... = ECN-Echo: Not set
        .... ..0. .... = Urgent: Not set
        .... ...1 .... = Acknowledgment: Set
        .... .... 1... = Push: Set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ·······AP···]
    Window size value: 229
    [Calculated window size: 29312]
    [Window size scaling factor: 128]
    Checksum: 0xcb58 [unverified]
    [Checksum Status: Unverified]
    Urgent pointer: 0
    Options: (12 bytes), No-Operation (NOP), No-Operation (NOP), Timestamps
    [SEQ/ACK analysis]
    [Timestamps]
    TCP payload (7 bytes)

## OSI Layers
Review the list of 10 suspicious activities and determine which of the seven OSI layers each falls under: <br>
A networking cable was cut in the data center and now no traffic can go out. **Physical**<br>
A code injection was submitted from an administrative website, and it's possible that an attacker can now see unauthorized directories from your Linux server. **Application**<br>
The MAC address of one of your network interface cards has been spoofed and is preventing some traffic from reaching its destination. **Data link**<br>
Your encrypted web traffic is now using a weak encryption cipher, and the web traffic is now vulnerable to decryption. **Presentation**<br>
The destination IP address was modified and traffic is routed to an unauthorized location. **Network**<br>
A flood of TCP requests is causing performance issues. **Transport**<br>
A SQL injection attack was detected by the SOC. This SQL injection may have deleted several database tables. **Application**<br>
A switch suddenly stopped working, and local machines aren't receiving any traffic. **Data link**<br>
An ethernet cable was disconnected, and the machine connected isn't able to receive any external traffic. **Physical**<br>
Traffic within the network is being directed from the switch to a suspicious device. **Data link**<br>

## Capturing Packets

Make the following configurations to your Wireshark application: <br>
Configure time to display the date and time of day so you can easily see when a certain activity occurs.<br>
Configure HTTP to display as a distinct color of your choice.<br>
Configure the network translation to display the webpage being accessed.<br>
Add additional columns, such as source and destination port.<br>
Remove the column "New Column."<br>

## Analyzing HTTP Data
