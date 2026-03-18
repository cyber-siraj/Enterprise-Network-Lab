# 🖧 Enterprise Network & SOC Monitoring Lab

## 🔹 Overview

This project simulates a small enterprise network with segmented departments, core network services, and basic SOC-style monitoring. The goal was to build a strong networking foundation before applying security concepts.

My approach is based on a simple principle: **you cannot secure what you do not understand**. By first learning how networks operate—how devices communicate, how traffic flows, and how services interact—I was able to begin thinking from a security and monitoring perspective.

---

## 🧱 Network Design

The network consists of:

- 1 Router (Inter-VLAN Routing)
- 1 Layer 2 Switch (VLAN segmentation)
- Multiple PCs (IT and Finance departments)
- 1 Core Server (DHCP, DNS, Syslog)

### 📸 Topology
![Topology](screenshots/1_topology.png.png)

---

## 🔌 VLAN Segmentation

Two VLANs were created to separate departments:

- **VLAN 10 — IT (192.168.10.0/24)**
- **VLAN 20 — Finance (192.168.20.0/24)**

Ports on the switch were manually assigned to each VLAN to isolate network traffic.

### 📸 VLAN Configuration
![VLAN](screenshots/2_vlan_config.png)

---

## 🌐 Inter-VLAN Routing

A router-on-a-stick configuration was implemented to allow communication between VLANs while maintaining segmentation.

- Subinterfaces configured on the router:
  - `192.168.10.1` (IT gateway)
  - `192.168.20.1` (Finance gateway)

---

## 📡 DHCP Configuration

Dynamic IP addressing was configured on the server for both VLANs.

### IT VLAN
- Network: `192.168.10.0/24`
- Gateway: `192.168.10.1`
- DNS: `192.168.10.2`

### 📸 DHCP (IT)
![DHCP IT](screenshots/3_dhcp_it.png)

---

### Finance VLAN
- Network: `192.168.20.0/24`
- Gateway: `192.168.20.1`
- DNS: `192.168.10.2`

### 📸 DHCP (Finance)
![DHCP Finance](screenshots/4_dhcp_finance.png)

---

## 🖥️ Server Configuration

The core server was configured with a static IP and used to host all network services.

- IP Address: `192.168.10.2`
- Services:
  - DHCP
  - DNS
  - Syslog

### 📸 Server IP Configuration
![Server IP](screenshots/5_server_ip.png)

---

## 🌍 DNS Configuration

A local DNS record was created to simulate internal name resolution:

- `company.local → 192.168.10.2`

This allows users to access services using a domain name instead of an IP address.

### 📸 DNS Configuration
![DNS](screenshots/6_dns_config.png)

---

## 📊 Syslog Monitoring (SOC Concept)

Basic network monitoring was implemented using syslog.

- Router logs are sent to the central server
- Configuration changes and system events are captured
- Simulates how network activity is monitored in a SOC environment

### 📸 Syslog Logs
![Syslog](screenshots/7_syslog_logs.png)

---

## 🔐 Security Perspective

This project demonstrates foundational security concepts:

- Network segmentation (VLANs)
- Controlled communication via routing
- Centralized logging for monitoring
- Visibility into system-level events

While Packet Tracer has limited logging capabilities, this lab represents the **core idea of a Security Operations Center (SOC)**:
monitoring network activity, analyzing events, and understanding system behavior.

---

## 🚀 Future Improvements

This project will be expanded to include:

- Access Control Lists (ACLs) for traffic filtering
- Simulated attack scenarios (ping sweeps, abnormal traffic)
- Advanced monitoring concepts
- Integration with SIEM tools (e.g., Splunk)

---

## 🧠 Key Takeaways

- Strong networking fundamentals are essential before diving into security
- Understanding traffic flow improves threat detection ability
- Monitoring and logging are critical components of cybersecurity
- Hands-on labs provide real-world context beyond theory

---

## 📌 Summary

This lab bridges the gap between networking and cybersecurity by combining infrastructure setup with basic monitoring concepts. It reflects a practical, step-by-step approach to building the skills required for entry-level IT.
