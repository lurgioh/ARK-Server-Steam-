# 🦖 ARK: Survival Evolved Dedicated Server (Headless Debian 13 Build)

## 📘 Project Overview
This project documents the complete setup, troubleshooting, and optimization process of hosting an **ARK: Survival Evolved** dedicated server on a self-built **Debian 13 headless Linux machine**.  
The goal was to create a stable, secure, and efficient server environment for Windows(Steam) of ARK, hosted on local hardware and remotely managed via SSH.

---

## 🧠 System Specs
| Component | Details |
|------------|----------|
| **CPU** | Intel Core i5-8400 (6 Cores / 6 Threads @ 4.0 GHz Boost) |
| **RAM** | 15 GB DDR4 |
| **Storage** | 120 GB SSD |
| **Operating System** | Debian 13 (Trixie) – Minimal / Headless Install |
| **Network** | Gigabit LAN |
| **Server Purpose** | ARK Dedicated Server for Xbox/Windows CrossPlay |

---

## ⚙️ Setup Process
### **1. OS Installation**
- Installed **Debian 13** from a USB stick using the text-based installer.  
- Selected **Guided partitioning – Use entire disk**.  
- Skipped GUI/Desktop environment for maximum performance.  
- Enabled **SSH server** and **standard system utilities** only.  
- **Did not set a root password** (to automatically grant sudo privileges to main user).  
- Created user **harrison** with a strong password for SSH and system administration.  

### **2. Network Configuration**
- Connected via Ethernet and automatically assigned IP: `192.168.1.234/24`  
- Verified network connectivity and confirmed DNS resolution.  

### **3. Remote Access Setup**
- Enabled SSH during installation.  
- Verified SSH service was active.  
- Connected from Windows laptop using SSH.  

---

## 🔧 Issues & Troubleshooting
### **Problem #1 – Terminal Freezing on Login**
- **Issue:** Terminal froze whenever `su -` was executed.  
- **Cause:** Corrupted system files and root misconfiguration from initial GUI install.  
- **Fix:** Reinstalled Debian with a minimal headless configuration (no desktop environment).  

### **Problem #2 – Missing Sudo Permissions**
- **Issue:** User `harrison` was not in the sudoers file; commands like `sudo systemctl` failed.  
- **Fix:** Installed `sudo` and added user to `sudo` group. Verified with `groups harrison` and `sudo whoami` returning `root`.  

### **Problem #3 – Corrupted Installation Media**
- **Issue:** Base package installation failed with errors such as *Failure while installing base packages*.  
- **Cause:** Faulty or incomplete Debian ISO image.  
- **Fix:** Re-downloaded Debian 13 ISO and re-flashed USB using **Rufus** (DD image mode).  

### **Problem #4 – BIOS Access / Boot Priority**
- **Issue:** Couldn’t access BIOS or boot menu; Debian launched directly.  
- **Fix:** Used **F8** and plugged in a keyboard with a cord and stopped using wireless keyboard 

### **Problem #5 – Network & SSH Confusion**
- **Issue:** Unclear if root password or domain name was required during setup.  
- **Fix:** Correct configuration used:  
  - Domain name: `local`  
  - Root password: *left blank for sudo setup*  
  - SSH server: *enabled during install*  
- Verified headless SSH access from another device.  

---

## 🚀 Final Configuration
- Updated and upgraded all packages.  
- Installed essential utilities: `curl`, `wget`, `screen`, `unzip`.  
- Installed **SteamCMD** for ARK server management.  
- Created a dedicated ARK server directory and downloaded the server files.  

---

## 🧩 Key Takeaways
- ⚙️ Running **headless Debian** significantly improves performance and stability.  
- 🧠 Learned advanced Linux privilege and user management (sudoers, root, user groups).  
- 🔐 Strengthened understanding of secure server setup and SSH administration.  
- 🧰 Improved problem-solving skills through multiple reinstalls and configuration recovery.  
- 🖥️ Gained hands-on experience building a reliable home game server from scratch.  

---

## 📈 Future Improvements
- Automate ARK startup with a `systemd` service.  
- Add monitoring via **Grafana + Prometheus**.  
- Implement offsite backups using `cron` jobs.  
- Enable secure remote access using **Tailscale** or **Cloudflare Tunnel**.  

---

## 🏁 Final Thoughts
This project involved several rounds of troubleshooting, OS reinstalls, and configuration refinement.  
Despite multiple challenges — including freezing terminals, sudo permission errors, and corrupt media — the final result was a **stable, secure, and headless ARK dedicated server** optimized for continuous uptime and remote management.  

This project strengthened my **Linux administration, troubleshooting, and server deployment skills**, and stands as a great representation of persistence and real-world problem-solving in a home lab environment.
