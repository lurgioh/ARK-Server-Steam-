# 🦖 ARK: Survival Evolved Dedicated Server (Bare Metal)

**Author:** Harrison Lurgio  
**Focus Areas:** Server Administration • Networking • Virtualization • Backup Automation  
**Status:** Active Project  

---

## 📖 Overview
This project documents the setup and operation of my **ARK: Survival Evolved dedicated server** hosted on **bare metal hardware**.  
The server is optimized for **Xbox Cross-Play**, managed through **AMP (Application Management Panel)**, and securely exposed to the internet via **Playit.gg tunneling** and **Tailscale** for remote administration.

I built this as part of my **homelab environment** to practice system deployment, uptime monitoring, and network isolation in a real-world gaming workload scenario.

---

## ⚙️ System Architecture

| Component | Description |
|------------|-------------|
| **Host OS** | Windows 10 Pro / Ubuntu Server 22.04 (bare metal) |
| **CPU** | Intel i5-8600 |
| **Memory** | 16 GB DDR4 |
| **Storage** | 1 TB SSD (server + OS), 2 TB HDD (backups) |
| **Network** | AT&T Fiber → Personal Router → Switch → Server |
| **Access** | Remote via Tailscale + Playit.gg Tunnel |
| **Management** | AMP (CubeCoders) |

**Topology Example:**


