# 🌐 CCNA 200-301 | Day 9: Switch Interfaces

## 🔌 Interface Speed and Duplex

Network efficiency depends on two primary settings configured on every switch port:

- **Speed:** Determines the data transmission rate (e.g., 10Mbps, 100Mbps, 1000Mbps).
    
- **Duplex:**
    
    - **Half Duplex:** The device cannot send and receive data simultaneously (similar to a Hub). It uses the **CSMA/CD** protocol to manage and prevent collisions.
        
    - **Full Duplex:** The device can send and receive data at the same time. This is the standard for modern switches.
        

---

## 🤝 Autonegotiation

Autonegotiation is a feature that allows two connected devices to exchange information about their speed and duplex capabilities and automatically agree on the highest performance settings supported by both.

### What happens during Autonegotiation Failure?

If autonegotiation is disabled on one side, the other side follows IEEE default rules:

1. **Speed:** The switch tries to sense the speed automatically. If it fails, it defaults to the slowest supported speed (usually 10Mbps).
    
2. **Duplex:**
    
    - If Speed is 10 or 100 Mbps $\rightarrow$ Defaults to **Half Duplex**.
        
    - If Speed is 1000 Mbps or higher $\rightarrow$ Defaults to **Full Duplex**.
        

> **⚠️ Duplex Mismatch:** If one side is set to Full and the other to Half, it results in interface errors, late collisions, and extremely slow performance.

---

## 📊 Interface Status

You can determine a port's health by looking at two specific columns in the command output:

- **Status:** Represents the **Physical Layer** (Layer 1).
    
- **Protocol:** Represents the **Data Link Layer** (Layer 2).
    

|**Status**|**Protocol**|**Meaning**|
|---|---|---|
|**up**|**up**|The interface is functional.|
|**down**|**down**|Physical issue (Cable unplugged or the other end is off).|
|**administratively down**|**down**|The port is manually disabled using the `shutdown` command.|
|**up**|**down**|Layer 2 issue (Rare on switches, common on Serial links).|

---

## 🛠️ Interface Counters & Errors

Use the `show interfaces [interface]` command to monitor port health and troubleshoot technical issues:

- **Runts:** Frames that are smaller than the minimum size (64 bytes).
    
- **Giants:** Frames that exceed the maximum size (1518 bytes).
    
- **CRC:** Indicates data was corrupted during transmission (usually due to a bad cable or electromagnetic interference).
    
- **Input Errors:** Total number of errors received on the interface.
    
- **Output Errors:** Total number of errors encountered during transmission.
    

---

## 💻 Command Summary

|**Command**|**Purpose**|
|---|---|
|`speed [10/100/1000]`|Manually sets the interface speed.|
|`duplex [full/half/auto]`|Manually sets the duplex mode.|
|`show interfaces status`|Displays a summary of all ports, their speed, and duplex.|
|`show interfaces [id]`|Displays detailed statistics and error counters.|