# 🖧 Enterprise Network & SOC Monitoring Lab

## 🔹 Overview

This project simulates a small enterprise network with segmented departments, essential network services, and basic SOC-style monitoring.

My approach is based on a key principle: **you cannot secure what you do not understand**. Before focusing on security, I built a strong foundation in networking—understanding how devices communicate, how traffic flows, and how core services operate. This allowed me to begin thinking from a security and monitoring perspective rather than just configuration.

---

## 🧱 Network Design

The network consists of:

- 1 Router (Inter-VLAN Routing)
- 1 Layer 2 Switch (VLAN segmentation)
- Multiple PCs (IT and Finance departments)
- 1 Core Server (DHCP, DNS, Syslog)

### 📸 Topology
![Topology](Network%20project/1_topology.png)

---

## 🔌 VLAN Segmentation

Two VLANs were created to separate departments and isolate traffic:

- **VLAN 10 — IT (192.168.10.0/24)**
- **VLAN 20 — Finance (192.168.20.0/24)**

Ports on the switch were manually assigned to each VLAN to enforce segmentation.

### 📸 VLAN Configuration
![VLAN](Network%20project/2_vlan_config.png)

---

## 🌐 Inter-VLAN Routing

A router-on-a-stick configuration was implemented to allow controlled communication between VLANs.

Subinterfaces configured on the router:

- `192.168.10.1` — IT Gateway  
- `192.168.20.1` — Finance Gateway  

---

## 📡 DHCP Configuration

Dynamic IP addressing was configured on the server for both VLANs.

### IT VLAN
- Network: `192.168.10.0/24`
- Gateway: `192.168.10.1`
- DNS: `192.168.10.2`

### 📸 DHCP (IT)
![DHCP IT](Network%20project/3_dhcp_it.png)

---

### Finance VLAN
- Network: `192.168.20.0/24`
- Gateway: `192.168.20.1`
- DNS: `192.168.10.2`

### 📸 DHCP (Finance)
![DHCP Finance](Network%20project/4_dhcp_finance.png)

---

## 🖥️ Server Configuration

The core server was configured with a static IP and used to host all network services.

- IP Address: `192.168.10.2`
- Services:
  - DHCP
  - DNS
  - Syslog

### 📸 Server Configuration
![Server](Network%20project/5_server_ip.png)

---

## 🌍 DNS Configuration

A local DNS record was created to simulate internal name resolution:

- `company.local → 192.168.10.2`

This allows users to access internal services using a domain name instead of an IP address.

### 📸 DNS Configuration
![DNS](Network%20project/6_dns_config.png)

---

## 📊 Syslog Monitoring (SOC Concept)

Basic monitoring was implemented using syslog:

- Router logs are forwarded to a centralized server
- Configuration changes and system events are captured
- Provides visibility into network activity

### 📸 Syslog Logs
![Syslog](Network%20project/7_syslog_logs.png)

---

## 🔐 Security Perspective

This project demonstrates foundational cybersecurity concepts:

- Network segmentation using VLANs
- Controlled communication via inter-VLAN routing
- Centralized logging for monitoring and visibility
- Awareness of system-level events

Although Packet Tracer has limited logging capabilities, this lab represents the **core concept of a Security Operations Center (SOC)**—collecting, monitoring, and analyzing network activity.

---

## 🚀 Future Improvements

This project will be expanded with:

- Access Control Lists (ACLs) for traffic filtering
- Simulated attack scenarios (ping sweeps, abnormal traffic)
- More advanced monitoring techniques
- Integration with SIEM tools such as Splunk

---

## 🧠 Key Takeaways

- Strong networking fundamentals are essential for cybersecurity
- Understanding traffic flow improves detection and troubleshooting
- Monitoring and logging are critical for security operations
- Hands-on labs provide real-world context beyond theory

---

## 📌 Summary

This lab bridges the gap between networking and cybersecurity by combining infrastructure setup with basic monitoring concepts. It reflects a practical, hands-on approach to building the foundational skills required for entry-level IT and SOC roles.
