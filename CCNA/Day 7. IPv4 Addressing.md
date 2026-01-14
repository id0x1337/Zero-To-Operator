

# 🌐 CCNA 200-301 | Day 7: IPv4 Addressing

## 🏗️ Layer 3: The Network Layer

The Network Layer is responsible for communication between different networks (outside the local LAN).

- **Logical Addressing:** Uses IP addresses to identify hosts.
    
- **Path Selection:** Determines the best path for data to travel across the internet.
    
- **Device:** **Routers** operate at Layer 3 and make decisions based on IP addresses.
    

---

## 🔢 IPv4 Structure & Binary Conversion

An IPv4 address is a **32-bit** logical address, divided into four **8-bit octets**.

### Address Formats:

- **Binary:** `11000000.10101000.00000001.11111110`
    
- **Dotted Decimal:** `192.168.1.254`
    

### Binary to Decimal Chart (The "Magic" Line):

To convert an octet, use these place values:

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |

---

## 🏛️ IPv4 Address Classes (Classful Addressing)

Historically, IP addresses were divided into classes based on the first octet.

|**Class**|**Range (First Octet)**|**Default Prefix**|**Leading Bits**|**Purpose**|
|---|---|---|---|---|
|**A**|0 - 127|`/8`|`0...`|Large Networks|
|**B**|128 - 191|`/16`|`10...`|Medium Networks|
|**C**|192 - 223|`/24`|`110...`|Small Networks|
|**D**|224 - 239|N/A|`1110...`|Multicast|
|**E**|240 - 255|N/A|`1111...`|Experimental|

> **Loopback Address:** `127.0.0.0/8` is reserved for testing the local network stack (e.g., `ping 127.0.0.1`).

---

## 🎭 Network vs. Host Portions

Every IP address consists of two parts:

1. **Network Portion:** Identifies the specific network (like a street name).
    
2. **Host Portion:** Identifies the specific device on that network (like a house number).
    

### Netmasks (Subnet Masks):

Used by devices to determine which bits belong to the network and which to the host.

- **Class A (/8):** `255.0.0.0`
    
- **Class B (/16):** `255.255.0.0`
    
- **Class C (/24):** `255.255.255.0`
    

---

## ⚠️ Special IPv4 Addresses

Within any network, two addresses **cannot** be assigned to hosts:

1. **Network Address:** * The host portion is **all 0s** in binary.
    
    - Represents the entire network (e.g., `192.168.1.0`).
        
2. **Broadcast Address:** * The host portion is **all 1s** in binary.
    
    - Used to send data to all hosts on the network (e.g., `192.168.1.255`).
        
    - Destination MAC for IP broadcasts: `FFFF.FFFF.FFFF`.
        

---

## 🛠️ Summary Table

|**Term**|**Definition**|
|---|---|
|**Octet**|A group of 8 bits.|
|**Prefix Length**|The number of network bits (e.g., `/24`).|
|**Unicast**|One-to-one communication.|
|**Broadcast**|One-to-all communication.|