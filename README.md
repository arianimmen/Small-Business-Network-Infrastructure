# 🏢 Small Business Network Infrastructure (GNS3 + Windows Server)

## 📘 Project Overview
This project simulates a small business network designed and implemented in **GNS3**.  
The goal is to demonstrate practical skills in **network design**, **VLAN segmentation**, **inter-VLAN routing**, and **Windows Server administration**.

The simulated environment includes multiple VLANs for different departments, a central router performing inter-VLAN routing (Router-on-a-Stick), and a Windows Server configured with Active Directory, DNS, and DHCP.

---

## 🎯 Objectives

* Design a realistic small company network topology
* Implement VLAN segmentation on a Cisco switch
* Configure Router-on-a-Stick for inter-VLAN routing
* Set up Windows Server with:

  * **Active Directory Domain Services** (PDC and ADC)
  * **DNS Server**
  * **DHCP Server**
  * **File Server with shared folders and ACLs**
  * **Group Policy configuration**
  * **User and group management using PowerShell**
* Implement backup strategy:

  * **System State backups** on S1
  * **Combined System State + shared folder backup** on S2
* Test and verify network connectivity, domain integration, and backup completion
* Document and version-control the project using **GitHub**
