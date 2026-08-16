# TechZone-Lab
EVE-NG | VMware | Cisco IOS | Windows Server 2022 | Ubuntu 22.04 | PowerShell | Syslog | NetFlow
# 🏢 TechZone - Integrated Enterprise Network Lab

A fully virtualized enterprise environment simulating a real-world company network, built from scratch using **EVE-NG** and **VMware Workstation**.

## 🎯 Project Objective
Design and implement a complete IT infrastructure that integrates:
- Cisco networking (Routing & Switching)
- Windows Server services (AD, DNS, DHCP, File Server)
- Linux systems (Client & Monitoring Server)
- Network monitoring (Syslog & NetFlow)
- Automation (PowerShell Backup Script)

---

## 🗺️ Network Topology
*(Insert your EVE-NG topology screenshot here)*

- **VLAN 10:** Clients (Windows 10, Ubuntu Client)
- **VLAN 20:** Servers (DC01, FILE01)
- **VLAN 30:** Monitoring (MONITOR Server)

---

## 📋 IP Addressing Scheme

| Device | Interface | IP Address | VLAN |
|--------|-----------|------------|------|
| R1 (Router) | G0/1.10 | 192.168.10.1 | 10 |
| R1 (Router) | G0/1.20 | 192.168.10.254 | 20 |
| R1 (Router) | G0/1.30 | 192.168.30.1 | 30 |
| DC01 | e0 | 192.168.10.10 (Static) | 20 |
| FILE01 | e0 | 192.168.10.20 (Static) | 20 |
| WIN10 | e0 | DHCP (10.100-200) | 10 |
| LINUX-CLI | e0 | DHCP | 10 |
| MONITOR | e0 | 192.168.30.100 (Static) | 30 |

---

## ⚙️ Services Configured

### 1. Networking (Cisco)
- **Router-on-a-stick** for Inter-VLAN routing.
- **DHCP Relay** to forward client requests to the Windows DHCP server.
- **Trunk** and **Access** ports on the switch.

### 2. Windows Server (DC01)
- **Active Directory** Domain Services (Domain: `techzone.local`).
- **DNS Server** and **DHCP Server**.
- Created OUs and users with **Group Policies (GPOs)** to map network drives.

### 3. File Server (FILE01)
- Shared folder with **NTFS permissions**.
- Accessible from both Windows and Linux clients via **CIFS**.

### 4. Linux Client (LINUX-CLI)
- Connected to the domain and mounted the shared folder using `cifs-utils`.

### 5. Monitoring Server (MONITOR - Ubuntu)
- **Syslog Server** (`rsyslog`) receiving logs from Router, Switch, and Windows Servers.
- **NetFlow Collector** (`nfdump`) analyzing traffic from the Cisco Router.

### 6. Automation (PowerShell)
- Automated daily backup script that pulls files from `FILE01` to `DC01`.
- Scheduled via **Task Scheduler** to run automatically at 2:00 AM daily.

---

## 🧪 Testing & Verification
- ✅ All devices can ping each other across VLANs.
- ✅ Windows 10 client can access `\\FILE01\Shared` (Z: Drive).
- ✅ Linux client mounts the share successfully.
- ✅ Syslog receives logs from network devices.
- ✅ `nfdump` displays live traffic data.

---

## 🛠️ Tools Used
- **EVE-NG** (Network Emulation)
- **VMware Workstation** (Hypervisor)
- **Cisco IOS** (Routing & Switching)
- **Windows Server 2022**
- **Ubuntu 22.04**
- **PowerShell**
- **Syslog / NetFlow**

---

## 📸 Screenshots
*(Insert screenshots here: Topology, DC01, WIN10 Z Drive, MONITOR nfdump output)*

---

## 🚀 Future Improvements
- Deploy **Zabbix** or **Prometheus** for advanced monitoring.
- Implement **Ansible** for configuration management.
- Add a **Firewall** (e.g., pfSense) for network security.

---

## 👨‍💻 Author
Abdallah Mohamed - [LinkedIn](https://www.linkedin.com/in/abdallah-mohamed-1928851b5)
