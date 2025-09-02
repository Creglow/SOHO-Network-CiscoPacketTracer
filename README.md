# 🌐 SOHO Network Project – Cisco Packet Tracer

## 📖 Overview
This project demonstrates how to design and configure a **Small Office/Home Office (SOHO) network** using **Cisco Packet Tracer**.  
The network is segmented into **departments using VLANs**, with inter-VLAN routing enabled on a router-on-a-stick setup.  
It also integrates **wireless access points and smartphones** to simulate a realistic office environment.  

The goal is to provide **a simple, scalable, and easy-to-understand design** that can be used for academic learning or as a reference for small businesses.

---

## 🖼️ Network Topology
![SOHO Topology](Diagrams/soho_network_topology.png)

The topology is designed with:
- **Router:** Cisco ISR 4331  
- **Switch:** Cisco Catalyst 2960  
- **Devices per VLAN:** One PC, one AP, one Smartphone  
- **Three VLANs:** IT, Finance, Customer Service  

---

## 🧩 VLAN & Subnet Design

| VLAN ID | Department         | Subnet              | Default Gateway     | SSID               |
|---------|--------------------|---------------------|---------------------|--------------------|
| 2       | IT                 | 192.168.1.0/26      | 192.168.1.1         | IT_WiFi            |
| 3       | Finance            | 192.168.1.64/26     | 192.168.1.65        | Finance_WiFi       |
| 4       | Customer Service   | 192.168.1.128/26    | 192.168.1.129       | CustService_WiFi   |

---

## ⚙️ Configurations

All configurations are provided in [`configs.txt`](configs.txt).  
Here’s a snapshot of the core setup:

### 🔹 Router (ISR4331)
```bash
interface g0/0/0
 no shut

interface g0/0/0.2
 encapsulation dot1Q 2
 ip address 192.168.1.1 255.255.255.192

interface g0/0/0.3
 encapsulation dot1Q 3
 ip address 192.168.1.65 255.255.255.192

interface g0/0/0.4
 encapsulation dot1Q 4
 ip address 192.168.1.129 255.255.255.192
