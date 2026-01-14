# CCNA 200-301 | Day 4: Cisco IOS CLI Basics

## 🖥️ What is a CLI?

The **Command-Line Interface (CLI)** is the text-based interface used to interact with and configure Cisco devices. Unlike a **GUI** (Graphical User Interface), the CLI is faster, more powerful, and essential for automation and remote management.

---

## 🔌 Connecting to a Cisco Device

To configure a Cisco device for the first time, you need a physical connection via the **Console Port**.

### Connection Methods:

1. **RJ45 Console Port:** Uses a **Rollover Cable** to connect to your PC.
    
2. **USB Mini-B Port:** A newer method using a standard USB cable.
    
3. **Terminal Emulator:** Software used on your PC to "talk" to the device.
    
    - **PuTTY** (The most common tool).
        

---

## 🛠️ Cisco IOS CLI Modes

The IOS (Internetwork Operating System) uses different modes to control access and configuration.

### 1. User EXEC Mode

- **Prompt:** `Router>`
    
- **Capability:** Very limited. You can view some status information but **cannot** change any configurations.
    
- **Security Tip:** This is the first line of defense; it provides "Read-Only" access.
    

### 2. Privileged EXEC Mode

- **Prompt:** `Router#`
    
- **How to enter:** Type `enable`.
    
- **Capability:** Provides full access to view configurations, restart the device, and manage files.
    
- **Note:** You still cannot change "global" settings here.
    

### 3. Global Configuration Mode

- **Prompt:** `Router(config)#`
    
- **How to enter:** From Privileged EXEC, type `configure terminal` (or `conf t`).
    
- **Capability:** This is where you actually **change** the device settings and behavior.
    

---

## ⌨️ CLI Navigation & Shortcuts

- **`?` (Question Mark):** Shows available commands in the current mode.
    
- **`Tab` Key:** Completes a partially typed command.
    
- **`no [command]`:** Used to cancel or remove a specific configuration.
    
- **`do [command]`:** Allows you to run Privileged EXEC commands while inside Global Config mode.
    

---

## 🔒 Securing Access (Passwords & Encryption)

### Enable Password vs. Enable Secret

- **`enable password [pass]`**: Sets a password to protect Privileged EXEC mode. Stored in **plain text** (Weak).
    
- **`enable secret [pass]`**: Sets a more secure password using **MD5 encryption**.
    
    - _Note: If both are set, the `enable secret` takes priority._
        

### Password Encryption

- **`service password-encryption`**: Encrypts all current and future plain-text passwords in the config file.
    
- **Warning:** It uses weak encryption that can be easily decrypted by a Red Teamer.
    

---

## 📂 Managing Configuration Files

Cisco devices maintain two separate configuration files:

1. **Running-config:**
    
    - Stored in **RAM**.
        
    - The active configuration. Changes take effect immediately.
        
    - Lost if the device restarts.
        
2. **Startup-config:**
    
    - Stored in **NVRAM**.
        
    - The configuration loaded when the device boots up.
        

### Commands to Know:

- **View active config:** `show running-config`
    
- **View saved config:** `show startup-config`
    
- **Save changes:** `copy running-config startup-config` (or simply `write`).
    

---

## 📝 Command Summary Table

|**Command**|**Mode**|**Description**|
|---|---|---|
|`enable`|User EXEC|Enter Privileged EXEC Mode|
|`configure terminal`|Privileged|Enter Global Configuration Mode|
|`hostname [name]`|Global Config|Change the device name|
|`enable secret [pass]`|Global Config|Set an encrypted privileged password|
|`service password-encryption`|Global Config|Encrypt all plain-text passwords|
|`show running-config`|Privileged|Display current active configuration|
|`write` / `copy run start`|Privileged|Save changes to NVRAM|
