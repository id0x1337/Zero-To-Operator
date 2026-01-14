	# 🌐 CCNA 200-301 | Day 5: Ethernet LAN Switching (Part 1)

## 🏗️ Layer 1 vs. Layer 2 Roles

Understanding the distinction between the physical and logical handling of data:

- **Layer 1 (Physical):** Defines physical characteristics (voltages, cables, connectors). Digital bits are converted into electrical or radio signals for transmission.
    
- **Layer 2 (Data Link):** Provides node-to-node connectivity and data transfer formatting. It detects physical layer errors and uses **MAC addressing** for delivery. **Switches** operate at this layer.
    

---

## 📦 The Ethernet Frame Structure

When data travels across a LAN, it is encapsulated into an **Ethernet Frame**.

|**Field**|**Size (Bytes)**|**Description**|
|---|---|---|
|**Preamble**|7|Alternating 1s and 0s for receiver clock synchronization.|
|**SFD**|1|Start Frame Delimiter; marks the beginning of the frame.|
|**Destination MAC**|6|Physical address of the receiving device.|
|**Source MAC**|6|Physical address of the sending device.|
|**Type / Length**|2|Indicates the protocol (IPv4/IPv6) or the packet length.|
|**Data (Packet)**|46 - 1500|The encapsulated Layer 3 Packet.|
|**FCS**|4|Frame Check Sequence; uses CRC to detect corruption.|

> **Note:** The total overhead (Header + Trailer) is **26 bytes**.

---

## 🆔 MAC Addresses (Physical Addressing)

- **Structure:** 6 bytes (48 bits) expressed as 12 hexadecimal characters.
    
- **Uniqueness:** Every device has a globally unique "Burned-In Address" (BIA).
    
- **OUI (Organizationally Unique Identifier):** The first 3 bytes, identifying the manufacturer.
    
- **Device ID:** The last 3 bytes, unique to that specific hardware.
    

---

## 🧠 How a Switch Works (Switching Logic)

Switches use a **MAC Address Table** (stored in RAM) to make forwarding decisions.

### 1. Learning (Populating the Table)

When a frame enters a port, the switch looks at the **Source MAC Address**.

- It records the MAC address and the interface (port) it came from.
    
- Dynamic entries are removed after **5 minutes** of inactivity.
    

### 2. Forwarding Decisions

The switch looks at the **Destination MAC Address**:

- **Known Unicast:** If the MAC is in the table, the switch **forwards** it out of the specific port.
    
- **Unknown Unicast:** If the MAC is NOT in the table, the switch **floods** the frame out of all ports except the incoming one.
    
- **Broadcast:** Sent to all ports (Destination: `FFFF.FFFF.FFFF`).