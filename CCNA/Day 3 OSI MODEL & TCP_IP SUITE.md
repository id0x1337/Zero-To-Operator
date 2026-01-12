# What is a networking model?
Networking models categorize and provide a structure for networking protocols and standards.

**Logical:**  
A set of rules defining how network devices and software should work.

---

# OSI Model
- "Open Systems Interconnection" model
- A conceptual model that categorizes and standardizes the different functions in a network
- Created by the International Organization for Standardization (ISO)
- Functions are divided into 7 layers
- These layers work together to make the network function

## Layer 7 — Application
- Closest to the end user
- Interacts with software applications (e.g., web browsers like Brave, Firefox, Chrome)
- Example protocols: HTTP, HTTPS

Functions:
- Identifying communication partners
- Synchronizing communication

## Layer 6 — Presentation
- Translates data between application format and network format
- Handles data encoding, encryption/decryption, and format translation (e.g., character encoding, compression)

## Layer 5 — Session
- Controls dialogues (sessions) between communicating hosts
- Establishes, manages, and terminates connections between local and remote applications

## Layer 4 — Transport
- Segments and reassembles data for communications between end hosts
- Breaks large pieces of data into smaller segments to reduce transmission errors
- Provides host-to-host communication (e.g., TCP, UDP)

When data from Layers 7–5 arrives, the Transport layer adds a Layer 4 header:

```
<< DATA + L4 Header >>
```

This unit is called a SEGMENT.

## Layer 3 — Network
- Provides connectivity between hosts on different networks (i.e., outside the LAN)
- Provides logical addressing (IP addresses)
- Handles path selection (routing)
- Devices: routers (operate at Layer 3)

When the Transport segment arrives, the Network layer adds a Layer 3 header:

```
<< DATA + L4 Header + L3 Header >>
```

This unit is called a PACKET.

## Layer 2 — Data Link
- Provides node-to-node (link) connectivity and data transfer (e.g., PC to switch)
- Defines how data is formatted for transmission over a physical medium (e.g., UTP cables)
- Detects and may correct Physical Layer errors
- Uses Layer 2 addressing (MAC addresses)
- Devices: switches (operate at Layer 2)

When the Network packet arrives, the Data Link layer adds a Layer 2 header and trailer:

```
<< L2 Header + DATA + L4 Header + L3 Header + L2 Trailer >>
```

This unit is called a FRAME.

All the steps adding headers/trailers before transmission are called ENCAPSULATION. When the frame is received, the reverse process (DE-ENCAPSULATION) strips off the Layer 2, Layer 3, then Layer 4 information as data ascends the stack.

## Layer 1 — Physical
- Defines physical characteristics of the medium used to transfer data between devices
- Examples: voltage levels, maximum transmission distances, connectors, cable specifications
- Converts digital bits into electrical (wired) or radio (wireless) signals

---

### OSI Model — PDUs (Protocol Data Units)

A PDU is the unit of data at each OSI layer.

| OSI Layer # | PDU Name | Protocol Data Added |
|-------------:|:--------:|:-------------------:|
| 7–5          | DATA     | Data                |
| 4            | SEGMENT  | Layer 4 header added|
| 3            | PACKET   | Layer 3 header added|
| 2            | FRAME    | Layer 2 header & trailer added |
| 1            | BIT      | 0s and 1s (physical transmission) |

Example encapsulation order:

```
<< L2 Header + DATA + L4 Header + L3 Header + L2 Trailer >>
```

---

# TCP/IP Suite
- A conceptual model and set of communications protocols used on the Internet
- Named after two foundational protocols: TCP and IP
- Developed from DARPA work (US DoD)
- Simpler than OSI; commonly used in real networks
- The OSI model still influences how engineers think and discuss networking concepts

## TCP/IP → OSI mapping (common view)
The TCP/IP model typically has 4 layers: Application, Transport, Internet, Link. OSI layers 7–5 are generally represented by the TCP/IP Application layer; OSI layers 2–1 correspond to the TCP/IP Link layer.

| OSI Layer # | OSI Name     | TCP/IP Layer # | TCP/IP Name  | Red Team Focus (examples)         |
|------------:|:-------------|:---------------:|:-------------|:----------------------------------|
| 7           | Application  | 4               | Application  | Web shells, phishing              |
| 6           | Presentation | 4               | Application  | Data encoding (Base64), encryption|
| 5           | Session      | 4               | Application  | Session hijacking                 |
| 4           | Transport    | 3               | Transport     | Port scanning (TCP/UDP)           |
| 3           | Network      | 2               | Internet      | IP spoofing, routing              |
| 2           | Data Link    | 1               | Link          | MAC flooding, ARP poisoning       |
| 1           | Physical     | 1               | Link          | Physical access, BadUSB           |

---

If تود أي تغيير إضافي (مثلاً: ترجمة المحتوى للعربية، إضافة أمثلة بروتوكولات مفصّلة، أو تحسين الجداول)، أخبرني ما الذي تريد تعديله تحديدًا. 
