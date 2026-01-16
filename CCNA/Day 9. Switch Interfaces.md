# 🌐 CCNA 200-301 | Day 9: Switch Interfaces

## 🛠️ Cisco CLI for Switches

Unlike routers, Cisco switch interfaces are **NOT** disabled (shutdown) by default. They are active as soon as they are powered on.

### Essential Interface Commands:

- `show ip interface brief`: Provides a quick summary of interface status (Layer 1) and protocol (Layer 2).
    
- `show interfaces status`: Displays a more detailed list including the name (description), VLAN, Duplex, Speed, and Port Type.
    

---

## ⚡ Interface Range (Bulk Configuration)

Unused interfaces pose a significant security risk. To secure a switch efficiently, you can configure a range of ports at once:

Bash

```
SW1(config)# interface range f0/5 - 12
SW1(config-if-range)# description ## NOT IN USE ##
SW1(config-if-range)# shutdown
```

> **Security Tip:** Best practice is to **shutdown** all unused ports to prevent unauthorized physical access to the network.

---

## 🏎️ Speed & Duplex Settings

### 1. Half vs. Full Duplex

- **Half Duplex:** The device cannot send and receive data at the same time. (Legacy/Hubs).
    
- **Full Duplex:** The device sends and receives data simultaneously, eliminating the need to wait.
    

### 2. CSMA/CD

A legacy mechanism used to manage **Collisions** in Half-Duplex environments:

1. **Carrier Sense:** Devices "listen" to the wire before sending.
    
2. **Collision Detection:** If two devices send at once, a collision occurs.
    
3. **Jamming Signal:** Devices detect the collision and send a signal to notify others.
    
4. **Backoff:** Each device waits for a random period before retrying.
    

---

## 🤝 Speed & Duplex Autonegotiation

Modern interfaces use `speed auto` and `duplex auto` by default. They "advertise" their capabilities to neighbors to agree on the best possible settings.

### Autonegotiation Failure (IEEE Rules):

If autonegotiation is disabled on the connected device:

- **Speed:** The switch tries to sense the speed; if unsuccessful, it defaults to the slowest supported speed (e.g., 10 Mbps).
    
- **Duplex:**
    
    - If speed is 10/100 Mbps $\rightarrow$ Defaults to **Half Duplex**.
        
    - If speed is 1000 Mbps or greater $\rightarrow$ Defaults to **Full Duplex**.
        

---

## 📊 Interface Counters & Errors

To monitor port health and troubleshoot performance issues, use: `show interfaces [interface_id]`.

### Key Error Counters:

- **Runts:** Frames smaller than the minimum 64-byte size (often caused by collisions).
    
- **Giants:** Frames larger than the maximum 1518-byte size.
    
- **CRC (Cyclic Redundancy Check):** Indicates the frame was corrupted during transmission (usually due to bad cabling or interference).
    
- **Input/Output Errors:** Total count of failed attempts to receive or send frames.
