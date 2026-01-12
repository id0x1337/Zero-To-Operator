🌐 Networking Models – Foundations
What is a Networking Model?

Networking models categorize and provide a structured framework for networking protocols and standards.

Logical Model

A logical model is a set of rules that defines how network devices and software should communicate and operate.

🧱 OSI Model

OSI = Open Systems Interconnection

Conceptual model that categorizes and standardizes network functions.

Created by the International Organization for Standardization (ISO).

Divides networking functions into 7 layers.

These layers work together to enable end-to-end communication.

7️⃣ Application Layer

Closest layer to the end user.

Interacts directly with software applications (e.g. browsers like Chrome, Firefox).

Examples of Layer 7 protocols:

HTTP

HTTPS

Functions:

Identifying communication partners

Synchronizing communication

6️⃣ Presentation Layer

Data at the Application Layer is in application-specific format.

This layer translates data into a format suitable for transmission.

Responsible for:

Encryption (before sending)

Decryption (upon receiving)

Data formatting and encoding

5️⃣ Session Layer

Manages sessions (dialogs) between communicating hosts.

Responsibilities:

Establishing connections

Maintaining sessions

Terminating sessions

Example:
Browser ↔ YouTube session management

4️⃣ Transport Layer

Provides host-to-host communication.

Breaks large data into smaller pieces for reliable transmission.

Handles:

Segmentation

Reassembly

Flow control

When data from Layers 7–5 arrives, a Layer 4 header is added:

[ DATA + L4 Header ]


➡️ This is called a SEGMENT.

3️⃣ Network Layer

Provides connectivity between hosts on different networks.

Responsibilities:

Logical addressing (IP addresses)

Path selection (routing)

Routers operate at this layer.

When the segment arrives, a Layer 3 header is added:

[ DATA + L4 Header + L3 Header ]


➡️ This is called a PACKET.

2️⃣ Data Link Layer

Provides node-to-node data transfer.

Defines how data is formatted for physical transmission.

Handles:

Error detection (and sometimes correction)

Layer 2 addressing (MAC addresses)

Switches operate at this layer.

When the packet arrives, a Layer 2 header and trailer are added:

[ L2 Trailer + DATA + L4 Header + L3 Header + L2 Header ]


➡️ This is called a FRAME.

🔁 Encapsulation

Adding headers/trailers while moving down the OSI layers.

The reverse process is De-encapsulation (Layer 1 → Layer 7).

1️⃣ Physical Layer

Defines the physical characteristics of data transmission.

Examples:

Voltage levels

Cable types

Connectors

Transmission distances

Converts digital bits into:

Electrical signals (wired)

Radio signals (wireless)

📦 OSI Model – PDU Names

A PDU (Protocol Data Unit) represents data at each OSI layer.

OSI Layer	PDU Name	Data Added
7–5	DATA	Application data
4	SEGMENT	Layer 4 Header
3	PACKET	Layer 3 Header
2	FRAME	Layer 2 Header + Trailer
1	BIT	0s and 1s transmission
🌍 TCP/IP Suite

Conceptual model + protocol suite used in the Internet.

Named after TCP and IP, its core protocols.

Developed by DARPA (US Dept. of Defense).

Uses fewer layers than the OSI model.

This is the model actually used in modern networks.

⚠️ Note:
The OSI Model is still used as a conceptual reference for learning and communication.

OSI vs TCP/IP (with Red Team Perspective)
OSI Layer	OSI Name	TCP/IP Layer	TCP/IP Name	Red Team Focus 🎯
7	Application	4	Application	Web Shells, Phishing
6	Presentation	4	Application	Encoding (Base64, Obfuscation)
5	Session	4	Application	Session Hijacking
4	Transport	3	Transport	Port Scanning (TCP/UDP)
3	Network	2	Internet	IP Spoofing, Routing Abuse
2	Data Link	1	Link	ARP Poisoning, MAC Flooding
1	Physical	—	—	Physical Access, BadUSB
