# Phase 2: DHCP Configuration on S1 (192.168.99.1)

## 📘 Goal
- Provide automatic IP addressing to all client VLANs (10, 20, 30, 99)  
- Ensure clients get correct **IP, subnet mask, default gateway, and DNS server**  
- Prepare network for **Active Directory domain integration** in Phase 3

---

## 🖥️ S1 Details
- Role: Primary Windows Server  
- VLAN: 99 (Servers)  
- Static IP: 192.168.99.1  
- Subnet Mask: 255.255.255.0  
- Default Gateway: 192.168.99.254  
- DNS Server: 192.168.99.1  

**Installed Roles:**
- DHCP Server
- DNS Server (preparing for Phase 3)
- Active Directory Domain Services (AD DS) – ready for domain promotion

---

## ⚙️ DHCP Configuration Steps

###  Install DHCP Role
1. Open **Server Manager → Add Roles and Features**  
2. Select **DHCP Server**  
3. Complete wizard and authorize DHCP in Active Directory  

###  Create DHCP Scopes

| VLAN | Scope Name | Network | Subnet Mask | Default Gateway | DNS Server |
|------|------------|---------|-------------|----------------|------------|
| 10   | HR        | 192.168.10.0 | 255.255.255.0 | 192.168.10.254 | 192.168.99.1 |
| 20   | IT        | 192.168.20.0 | 255.255.255.0 | 192.168.20.254 | 192.168.99.1 |
| 30   | Guest     | 192.168.30.0 | 255.255.255.0 | 192.168.30.254 | 192.168.99.1 |
| 99   | Server    | 192.168.99.0 | 255.255.255.0 | 192.168.99.254 | 192.168.99.1 |

> **Note:** No superscope is required since the router forwards DHCP requests using `ip helper-address` (DHCP Relay Agent is acitve on R1).

<img width="1077" height="383" alt="image" src="https://github.com/user-attachments/assets/5064986a-25e5-4d37-a9a5-75e20a7e6ad3" />
 

### 3️⃣ Configure Router DHCP Relay
On R1:

```bash
interface GigabitEthernet0/0.10
 ip helper-address 192.168.99.1
interface GigabitEthernet0/0.20
 ip helper-address 192.168.99.1
interface GigabitEthernet0/0.30
 ip helper-address 192.168.99.1
interface GigabitEthernet0/0.99
 ip helper-address 192.168.99.1
