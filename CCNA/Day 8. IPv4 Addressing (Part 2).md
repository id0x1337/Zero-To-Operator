# 🌐 CCNA 200-301 | Day 8: IPv4 Addressing (Part 2)

## 🧮 Calculating Network Parameters

To manage a network, you must be able to calculate its boundaries. The key formula for finding the number of available hosts is:

> $2^n - 2$
> 
> (where $n$ is the number of host bits)

### Why subtract 2?

1. **-1 for the Network Address:** (Host portion is all **0s**).
    
2. **-1 for the Broadcast Address:** (Host portion is all **1s**).
    

### Summary of Classful Limits:

|**Class**|**Prefix**|**Host Bits (n)**|**Max Usable Hosts**|
|---|---|---|---|
|**Class A**|`/8`|24|$2^{24} - 2 = 16,777,214$|
|**Class B**|`/16`|16|$2^{16} - 2 = 65,534$|
|**Class C**|`/24`|8|$2^8 - 2 = 254$|

---

## 📍 Finding Address Ranges (Example: 192.168.1.0/24)

- **Network Address:** `192.168.1.0` (The ID of the network).
    
- **First Usable:** `192.168.1.1` (Network ID + 1).
    
- **Last Usable:** `192.168.1.254` (Broadcast ID - 1).
    
- **Broadcast Address:** `192.168.1.255` (The address used to talk to everyone).
    

---

## ⚙️ Configuring IP Addresses on Cisco IOS

On a Cisco router, interfaces are **Disabled (Shutdown)** by default. You must manually enable them.

### Basic Configuration Steps:

1. Enter Interface Mode:
    
    Router(config)# interface [interface_name] (e.g., g0/0)
    
2. Assign IP & Mask:
    
    Router(config-if)# ip address [address] [mask]
    
3. Activate Interface:
    
    Router(config-if)# no shutdown
    
4. Add Description (Optional but Recommended):
    
    Router(config-if)# description [text]
    

---

## 🔍 Verification Commands

To ensure your configuration is correct and the hardware is functioning:

- **`show ip interface brief`**: Provides a quick summary of all interfaces, their IPs, and their status.
    
- **`show interfaces [interface]`**: Provides detailed statistics (MTU, Bandwidth, MAC, etc.).
    
- **`show interfaces description`**: Displays the descriptions you assigned to each port.
    

### Interface Status Meanings:

- **Status: Up / Protocol: Up**: The interface is working (Layer 1 and Layer 2 are functional).
    
- **Status: Administratively Down**: The `shutdown` command is active on the interface.
    
- **Status: Down / Protocol: Down**: Physical layer issue (e.g., cable is unplugged).
    

---

## 🛠️ Command Summary Cheat Sheet

| **Command**              | **Purpose**                                       |
| ------------------------ | ------------------------------------------------- |
| `int [name]`             | Move to interface configuration mode.             |
| `ip address [ip] [mask]` | Assign an IPv4 address to the interface.          |
| `no shutdown`            | Enables the interface (Bring it up).              |
| `sh ip int brief`        | Check IP and Up/Down status of all ports.         |
| `sh run`                 | View the entire configuration file including IPs. |