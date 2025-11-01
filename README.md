# 🦖 ARK: Survival Evolved Dedicated Server (Headless Debian 13 Build)

## 📘 Project Overview
This project documents the complete setup, troubleshooting, and optimization process of hosting an **ARK: Survival Evolved** dedicated server on a self-built **Debian 13 headless Linux machine**.  
The goal was to create a stable, secure, and efficient server environment for **Xbox/Windows CrossPlay (Microsoft version)** of ARK, hosted on local hardware and remotely managed via SSH and AMP.

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
- Used a **wired USB keyboard** for BIOS access because the Bluetooth keyboard was not detected during POST, preventing BIOS entry.

### **2. Network Configuration**
- Connected via Ethernet and automatically assigned IP: `192.168.1.234/24`.  
- Verified network connectivity and confirmed DNS resolution.  

### **3. Remote Access Setup**
- Enabled SSH during installation.  
- Verified SSH service was active.  
- Connected from Windows laptop using SSH (`ssh harrison@192.168.1.234`).  

---

## 🔧 Issues & Troubleshooting
### **Problem #1 – Terminal Freezing on Login**
- **Issue:** Terminal froze whenever `su -` was executed.  
- **Cause:** Corrupted system files and root misconfiguration from initial GUI install.  
- **Fix:** Reinstalled Debian with a minimal headless configuration (no desktop environment).  

### **Problem #2 – Missing Sudo Permissions**
- **Issue:** User `harrison` was not in the sudoers file; commands like `sudo systemctl` failed.  
- **Fix:** Installed `sudo` and added the user to the `sudo` group. Verified with `groups harrison` and `sudo whoami` returning `root`.  

### **Problem #3 – Corrupted Installation Media**
- **Issue:** Base package installation failed with errors such as *Failure while installing base packages*.  
- **Cause:** Faulty or incomplete Debian ISO image.  
- **Fix:** Re-downloaded Debian 13 ISO and re-flashed USB using **Rufus** (DD image mode).  

### **Problem #4 – BIOS Access / Boot Priority**
- **Issue:** Could not access BIOS or boot menu because Bluetooth keyboard failed to register before POST.  
- **Fix:** Switched to a **wired keyboard**, pressed **F8** during startup, and accessed BIOS/boot menu successfully.  

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
- Installed essential utilities (`curl`, `wget`, `screen`, `unzip`).  
- Installed **SteamCMD** for ARK server management.  
- Created a dedicated ARK server directory and downloaded the server files.  

---

## 🧩 Installing AMP (Application Management Panel)
After the ARK server was configured manually, **AMP** was installed to simplify management and automate tasks.

### **What AMP Does**
AMP (Application Management Panel) is a lightweight web-based interface for managing game servers, services, and applications.  
It handles:
- Game server installation and updates  
- Service monitoring  
- Scheduled backups and restarts  
- Easy configuration through a web UI  

### **Installation Summary**
1. Added AMP repository and installed dependencies.  
2. Installed AMP using the official CubeCoders script.  
3. Configured a new **ARK: Survival Evolved instance** within AMP.  
4. Set resource limits, scheduled auto restarts, and verified successful startup through the web dashboard.  
5. Secured AMP with authentication and confirmed accessibility via local IP in browser (port 8080 by default).  

**Result:** AMP provided centralized management, logging, and streamlined configuration for the ARK server, improving efficiency and stability.

---

## 🧠 Key Takeaways
- ⚙️ Running **headless Debian** significantly improved performance and resource utilization.  
- 🧰 Troubleshot multiple Linux issues including privilege escalation, freezing terminals, and corrupted installations.  
- 🧠 Learned advanced privilege and service management (sudoers, systemctl, SSH, AMP).  
- 🔐 Strengthened understanding of secure and modular game server hosting.  
- 💡 Adapted quickly — switching from a Bluetooth to wired keyboard to regain BIOS control.  
- 🕹️ Gained real-world experience hosting and maintaining a production-style game server environment.  

---

## 📈 Future Improvements
- Automate ARK startup through a `systemd` service integrated with AMP.  
- Add monitoring via **Grafana + Prometheus** dashboards.  
- Implement offsite backups using `rsync` and cron jobs.  
- Set up **Tailscale** or **Cloudflare Tunnel** for secure remote management.  

---

## 🏁 Final Thoughts
This project involved multiple reinstalls, BIOS troubleshooting, network configuration, and service management learning.  
Despite recurring challenges — from keyboard issues and sudo errors to corrupt media — the end result is a **fully functional, secure, and headless ARK dedicated server** running on Debian 13 and managed through AMP.  

This process strengthened my **Linux administration, troubleshooting, automation, and homelab deployment skills**, and showcases persistence, adaptability, and deep problem-solving in a real-world scenario.
