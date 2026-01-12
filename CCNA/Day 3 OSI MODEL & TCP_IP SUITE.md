
## What is a networking model?
Networking models categorize and provide a structure for networking protocols and standards.

### logical
A set of rules defining how network devices and software should work.


# OSI Model 
● ‘Open Systems Interconnection’ model 
● A conceptual model that categorizes and standardizes the different functions in a network. 
● Created by the ‘International Organization for Standardization’ (ISO). 
● Functions are divided into 7 ‘Layers’. 
● These layers work together to make the network work


## 7. Application Layer
● This layer is closest to the end user. 
● Interacts with software applications, for example your web browser (Brave, Firefox, Chrome, etc) ● HTTP and HTTPS are Layer 7 protocols (https://www.cisco.com) 

Functions of Layer 7 include:
● Identifying communication partners 
● Synchronizing communication

## 6. Presentation Layer
●Data in the application layer is in ‘application format’.
● It needs to be ‘translated’ to a different format to be sent over the network.
● The Presentation Layer’s job is to translate between application and network formats.
● For example, encryption of data as it is sent, and decryption of data as it is received. 
●Also translates between different Application Layer formats.


## 5. Session Layer
● Controls dialogues (sessions) between communicating hosts. 
● Establishes, manages, and terminates connections between the local application (for example, your web browser) and the remote application (for example, YouTube).

## 4. Transport Layer
● Segments and reassembles data for communications between end hosts. 
●Breaks large pieces of data into smaller segments which can be more easily sent over the network and are less likely to cause transmission problems if errors occur. 
●Provide host-to-host communication.

When Data from Layer 7-5 arrives, it receives a Layer 4 Header in the Transport layer.

<< DATA + L4 Header >>

This is called a SEGMENT.


## 3. Network Layer
●Provides connectivity between end hosts on different networks (ie. outside of the LAN). ●Provides logical addressing (IP addresses). 
●Provides path selection between source and destination. 
●Routers operate at Layer 3.

When Data and the Layer 4 Header arrive in the Network Layer, it receives a Layer 3 Header.

<< DATA + L4 Header + L3 Header >>

This is called a **PACKET**.


## 2. Data Link Layer
Provides node-to-node connectivity and data transfer (for example, PC to switch, switch to router, router to router). 
●Defines how data is formatted for transmission over a physical medium (for example, copper UTP cables) 
●Detects and (possibly) corrects Physical Layer errors. 
●Uses Layer 2 addressing, separate from Layer 3 addressing. 
● Switches operate at Layer 2.

When the Layer 3 Packet arrives, a Layer 2 Trailer and Header are added.

<< L2 Trailer + DATA + L4 Header + L3 Header + L2 Header >>

This is called a FRAME.

All the steps leading up to transmission is called ENCAPSULATION. When the frame is sent to the receiver, it then goes through the reverse process, DE-ENCAPSULATION, stripping off layers while travelling from OSI Layer 1 to Layer 7.

## 1. Physical Layer
●Defines physical characteristics of the medium used to transfer data between devices. 
● For example, voltage levels, maximum transmission distances, physical connectors, cable specifications, etc. 
●Digital bits are converted into electrical (for wired connections) or radio (for wireless connections) signals.


### OSI MODEL - PDU's

A PDU is a Protocol Data Unit. Each step of the process is a PDU.

|OSI LAYER #|PDU NAME|PROTOCOL DATA ADDED|
|---|---|---|
|7-5|DATA|Data|
|4|SEGMENT|Layer 4 Header Added|
|3|PACKET|Layer 3 Header Added|
|2|FRAME|Layer 2 Trailer and Header Added|
|1|BIT|0s and 1s Transmission|

<< L2 Trailer + DATA + L4 Header + L3 Header + L2 Header >>

### TCP/IP Suite

- Conceptual model and set of communications protocols used in the Internet and other networks.
- Known as TCP/IP because those are two of the foundational protocols in the suite.
- Developed by the US Dept. of Defense through DARPA (Defense Advanced Research Projects Agency).
- Similar structure to the OSI Model, but fewer layers.
- THIS is the model actually in use in modern networks.
- - Note : The OSI Model still influences how network engineers think and talk about networks.

| **OSI Model Layer** | **OSI Name**     | **TCP/IP Layer** | **TCP/IP Name** | **Red Team Focus 🎯**           |
| ------------------- | ---------------- | ---------------- | --------------- | ------------------------------- |
| **7**               | **Application**  |                  |                 | **Web Shells, Phishing**        |
| **6**               | **Presentation** | **4**            | **Application** | **Data Encoding (Base64)**      |
| **5**               | **Session**      |                  |                 | **Session Hijacking**           |
| **4**               | **Transport**    | **3**            | **Transport**   | **Port Scanning (TCP/UDP)**     |
| **3**               | **Network**      | **2**            | **Internet**    | **IP Spoofing, Routing**        |
| **2**               | **Data Link**    | **1**            | **Link**        | **MAC Flooding, ARP Poisoning** |
| **1**               | **Physical**     |                  |                 | **Physical Access, BadUSB**     |