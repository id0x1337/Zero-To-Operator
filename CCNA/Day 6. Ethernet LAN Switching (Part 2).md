
# 🌐 CCNA 200-301 | Day 6: Ethernet LAN Switching (Part 2)

## 📦 Ethernet Frame: Size and Padding

Beyond the basic structure, the Ethernet frame has specific size constraints that impact how data is transmitted.

- **Header & Trailer Size:** While the Preamble and SFD are part of the transmission, they are generally not counted in the 18-byte Header (14 bytes) + Trailer (4 bytes) total.
    
- **Minimum Frame Size:** The minimum size for an Ethernet frame is **64 bytes**.
    
- **Minimum Payload (Packet):** 64 bytes (Minimum Frame) - 18 bytes (Overhead) = **46 bytes**.
    
- **Padding:** If the Layer 3 packet is smaller than 46 bytes, the system adds **Padding bytes** (usually zeros) to reach the 46-byte minimum.
    

---

## 🔍 ARP (Address Resolution Protocol)

ARP is the "bridge" between Layer 3 (IP) and Layer 2 (MAC). It is used to find a MAC address when only the IP address is known.

### The ARP Process:

1. **ARP Request (Broadcast):** PC1 sends a message to **FFFF.FFFF.FFFF** asking, _"Who has IP 192.168.1.3? Tell 192.168.1.1."_ Every device in the LAN receives this.
    
2. **ARP Reply (Unicast):** The device with the matching IP responds directly to PC1 with its MAC address.
    

### ARP Table (ARP Cache):

Devices store discovered mappings in an **ARP Table** to avoid repeated requests.

- **Command (Windows/Linux/MacOS):** `arp -a`
    
- **Dynamic Entry:** Learned via the network; expires after a period of inactivity.
    
- **Static Entry:** Manually entered; does not expire.
    

---

## 🛰️ Ping & ICMP

**Ping** is a utility used to test the reachability of a host on an IP network.

- **Protocol:** Uses **ICMP** (Internet Control Message Protocol).
    
- **Mechanism:**
    
    - **ICMP Echo Request:** Sent by the source to the target.
        
    - **ICMP Echo Reply:** Sent by the target back to the source.
        
- **Measurement:** Reports the **Round-Trip Time (RTT)**.
    

---

## 🧠 Switch MAC Address Table Management

Switches must manage their memory efficiently to handle changing network topologies.

- **Aging:** Dynamic entries are kept for **5 minutes** (default) of inactivity before being flushed.
    
- **Switching Behavior (Recap):**
    
    - **Flood:** Broadcast frames and Unknown Unicast frames are sent out all ports except the source.
        
    - **Forward:** Known Unicast frames are sent only to the specific destination port.
        

### Cisco IOS Commands:

- **View Table:** `show mac address-table`
    
- **Clear Table:** `clear mac address-table dynamic`
    
- **Clear Specific Port:** `clear mac address-table dynamic interface [interface-id]`
    

---

## 🛠️ Command Summary

|**Task**|**Command**|**Context**|
|---|---|---|
|**View ARP Cache**|`arp -a`|PC (CMD/Terminal)|
|**Test Connectivity**|`ping [IP_Address]`|PC/Router/Switch|
|**View MAC Table**|`show mac address-table`|Cisco Switch|
|**Clear MAC Table**|`clear mac address-table dynamic`|Cisco Switch|