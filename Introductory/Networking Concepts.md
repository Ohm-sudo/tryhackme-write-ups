<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/5f04259cf9bf5b57aed2c476-1719330093098" alt="Room Icon" width="200"/>
</p>

# Networking Concepts
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/strategos">strategos</a>, <a href="https://tryhackme.com/p/Gensane">Gensane</a>

<br>

## Task 2: OSI Model
- OSI (Open Systems Interconnection) model is a conceptual model developed by ISO (International Organization for Standardization).
- Describes communications in a computer network.
- Seven layers:
  1. Physical Layer
  2. Data Link Layer
  3. Network Layer
  4. Transport Layer
  5. Session Layer
  6. Presentation Layer
  7. Application Layer
- Can use a mnemonic such as "Please Do Not Throw Spinach Pizza Away" to remember.

<br>

### Layer 1: Physical Layer
- Physical connection between devices (i.e., wire, binary digits 0 and 1).
- Data transmission can be electrical, optical, or wireless signal.
- Cables or antennas.
- Examples: Ethernet cable, optical fibre cable, WiFi radio bands.

### Layer 2: Data Link Layer
- Represents protocol that enables data transfer between network nodes (in same segment).
  - A network segment would be like a group of networked devices in an office.
- Examples: 802.3 (Ethernet), 802.11 (Wi-Fi), MAC Address (Media Access Control).

### Layer 3: Network Layer
- Handles sending of data between different networks.
  - i.e., Connecting between different offices from around the world.
- Examples: IP, ICMP, VPN (IPSec, SSL/TLS).

### Layer 4: Transport Layer
- Enables end-to-end communication between applications on different hosts.
- Flow control, segmentation, and error correction.
- Examples: TCP, UDP

### Layer 5: Session Layer
- Establishes, maintains, and synchronizes communication between applications running on different hosts.
- Examples: Network File System (NFS), Remote Procedure Call (RPC).

### Layer 6: Presentation Layer
- Ensures data is presented in a way that the application layer can understand.
- Handles encoding, compression, and encryption.
- Examples: MIME, JPEG, GIF, PNG

### Layer 7: Application Layer
- Provides network services to end-user applications.
- Examples: HTTP, FTP, DNS, POP3, SMTP, and IMAP.

<br>

#### Q1: Which layer is responsible for end-to-end communication between running applications?
<pre>4</pre>
Transport layer handles end-to-end communication.

<br>

#### Q2: Which layer is responsible for routing packets to the proper network?
<pre>3</pre>
Network layer is responsible for routing packets.

<br>

#### Q3: In the OSI model, which layer is responsible for encoding the application data?
<pre>6</pre>
Session layer is responsible for encoding application data.

<br>

#### Q4: Which layer is responsible for transferring data between hosts on the same network segment?
<pre>2</pre>
Data link layer is responsible for transferring data between hosts on same network segment.

<br>

## Task 3: TCP/IP Model
- TCP/IP stands for Transmission Control Protocol/Internet Protocol.
- Developed in 1970s by the Department of Defense (DoD).
- RFC 1122
- Layers:
  - Application Layer: Layers 5, 6, 7 from OSI grouped here.
  - Transport Layer: Layer 4.
  - Internet Layer: Layer 3.
  - Link Layer: Layer 2
 
<br>

#### Q1: To which layer does HTTP belong in the TCP/IP model?
<pre>Application layer</pre>
<br>

#### Q2: How many layers of the OSI model does the application layer in the TCP/IP model cover?
<pre>3</pre>
Covers session, presentation, and application layer.

<br>

## Task 4: IP Addresses and Subnets
- An IP address is a unique identifier for hosts connected to a network or Internet.
  - An analogy is your home postal address.
- Comprised of four octets (32 bits). One octet is 8 bits - allows us to represent a decimal number (0-255).
- 0 and 255 reserved for network and broadcast addresses, respectively.
  - i.e., 192.168.1.0 is the network address, 192.168.1.255 is the broadcast address.
- On Windows, can use ```ipconfig``` to look up your IP. On Linux or UNIX-based systems, use ```ifconfig or ip address show```.

### Private Addresses
- Ranges of private IP addresses (RFC 1918):
  - ```10.0.0.0``` - ```10.255.255.255``` (10.x.x.x/8)
  - ```172.16.0.0``` - ```172.31.255.255``` (172.16.x.x/12)
  - ```192.168.0.0``` - ```192.168.255.255``` (192.168.x.x/16) 

### Routing
- Router is like a local post office - know how to deliver.
- Forward data packets to network.

<br>

#### Q1: Which of the following IP addresses is not a private IP address?

- 192.168.250.125
- 10.20.141.132
- 49.69.147.197
- 172.23.182.251

<pre>49.69.147.197</pre>
The IP address above does not fall under any of the private IP address ranges.

<br>

#### Q2: Which of the following IP addresses is not a valid IP address?

- 192.168.250.15
- 192.168.254.17
- 192.168.305.19
- 192.168.199.13

<pre>192.168.305.19</pre>
In number in the 3rd octet of the above IP address is invalid. Should only be 0-255.

<br>

## Task 5: UDP and TCP
### UDP
- User Datagram Protocol.
- Simple, connectionless protocol.
- Does not need to establis hconnection. Doesn't know if packet has been delivered.
- Port numbers are used to determine sending and receiving process.

### TCP
- Transimission Control Protocol.
- Connection-oriented protocol.
- Ensures reliable data delivery.
- Connection is established using three-way handshake:
  1. SYN Packet: Client initiates connection. Contains client's random sequence number.
  2. SYN-ACK Packet: Server responds to SYN with SYN-ACK packet.
  3. ACK Packet: Three-way handshake complete. Client sends ACK packet to acknowledge.
 
<br>

#### Q1: Which protocol requires a three-way handshake?
<pre>TCP</pre>
<br>

#### Q2: What is the approximate number of port numbers (in thousands)?
<pre>65</pre>
Valid port number ranges are between 1 and 65535.

<br>

## Task 6: Encapsulation
- Process of every layer adding a header (sometimes a trailer) and sending "encapsulated" unit to layer below.
1. Start with application data.
2. At transport layer, add TCP or UDP header to create TCP **segment** or UDP **datagram**.
3. At network layer, add IP header to get IP **packet** that can be routed over Internet.
4. Add appropriate header and trailer to get Wi-Fi or Ethernet **frame** at link layer.
- Process is reversed on the receiving end until application data extracted.

<br>

#### Q1: On a WiFi, within what will an IP packet be encapsulated?
<pre>Frame</pre>
WiFi is layer 2. At layer 2 this is described as a frame.

#### Q2: What do you call the UDP data unit that encapsulates the application data?
<pre>Datagram</pre>
UDP is layer 4. At layer 4 this is described as a datagram.

#### Q3: What do you call the data unit that encapsulates the application data sent over TCP?
<pre>Segment</pre>
TCP is layer 4. At layer 4 this is described as a segment.

<br>

## Task 7: Telnet
- Telnet (Teletype Network) is a protocol for remote terminal connection.
- Connect and communicate with remote system and issue commands.
- For this room, there are 3 services we will be experimenting with:
  - Echo server: Echoes everything you send it. Listens on port 7.
  - Daytime server: Listens on port 13 and replies with date and time.
  - Web (HTTP) server: Listens on TCP port 80 and serves web pages.
- Telnet syntax: ```telnet <TARGET_IP> <PORT_NUMBER>```

<br>

#### Q1: Use ```telnet``` to connect to the web server on ```MACHINE_IP```. What is the name and version of the HTTP server?
<pre>lighttpd/1.4.63</pre>
<br>

#### Q2: What flag did you get when you viewed the page?
<pre>THM{TELNET_MASTER}</pre>
