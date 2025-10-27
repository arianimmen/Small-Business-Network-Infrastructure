# 🏢 Small Business Network Infrastructure (GNS3 + Windows Server)

## 📘 Project Overview
This project simulates a small business network designed and implemented in **GNS3**.  
The goal is to demonstrate practical skills in **network design**, **VLAN segmentation**, **inter-VLAN routing**, and **Windows Server administration**.

The simulated environment includes multiple VLANs for different departments, a central router performing inter-VLAN routing (Router-on-a-Stick), and a Windows Server configured with Active Directory, DNS, and DHCP.

---

## 🎯 Objectives
- Design a realistic small company network topology
- Implement VLAN segmentation on a Cisco switch
- Configure Router-on-a-Stick for inter-VLAN routing
- Set up Windows Server with:
  - **Active Directory Domain Services**
  - **DNS Server**
  - **DHCP Server**
- Test and verify network connectivity and domain integration
- Document and version-control the project using **GitHub**

---

## 🗺️ Phase 1  (Network Design) 
The company network consists of one main switch, one router, and a Windows Server for network services.  
All PCs and servers are connected to the switch, which uses VLANs to separate departments.  
The router provides communication between VLANs via subinterfaces.

**Topology Diagram:**  
<img width="1020" height="625" alt="image" src="https://github.com/user-attachments/assets/a781dca9-7f42-47db-bd56-1d390be4d6fe" />


---

## 🧩 VLAN Table

| VLAN | Name        | Purpose         | Subnet              |
|------|--------------|-----------------|---------------------|
| 10   | IT           | IT & Servers    | 192.168.10.0/24     |
| 10   | HR           | HR staffs       | 192.168.20.0/24     |
| 30   | Staff        | Other Staffs    | 192.168.30.0/24     |
| 99   | Servers      | Admin Access    | 192.168.99.0/24     |

---

## ⚙️ Configuration Summary

### **Router (R1)**
- Router-on-a-Stick configuration  
- Subinterfaces for VLANs 10, 20, 30, and 99  
- Each subinterface assigned the default gateway for its VLAN  
- Connected via trunk link to the switch

### **Switch (SW1)**
- VLANs created: 10, 20, 30, 99  
- Access ports assigned to the correct VLAN  
- Trunk port (Gi1/0) connected to router for VLAN tagging  
- Management VLAN (99) used for switch administration  

