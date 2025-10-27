# Phase 3: Active Directory and DNS Integration

## 📘 Goal

* Promote **Server1** to **Domain Controller (AD DS)**
* Join client PCs to the domain
* Configure **internal DNS** for hostname resolution
* Add **Server2** as a secondary Domain Controller (ADC) for redundancy
* Ensure centralized authentication and proper DNS resolution across VLANs

---

## 🖥️ Server Details

| Server  | Role                    | VLAN     | IP Address    | Notes                        |
| ------- | ----------------------- | -------- | ------------- | ---------------------------- |
| S1      | Primary DC / DNS / DHCP | 99       | 192.168.99.1  | Main domain controller       |
| S2      | ADC / Backup DNS        | 10       | 192.168.10.2  | Secondary domain controller  |
| Clients | Workstation            | 10/20/30 | DHCP          | Join domain `immen.com` |

---

## ⚙️ Step 1: Promote Server1 to Domain Controller

1. Open **Server Manager → Add Roles → Active Directory Domain Services**
2. Complete the wizard:

   * **Deployment:** New forest
   * **Domain Name:** `immen.com`
   * Install **DNS server role**
3. Reboot after promotion
4. Server1 now acts as **primary domain controller (DC)** and authoritative DNS server

   <img width="922" height="331" alt="image" src="https://github.com/user-attachments/assets/b29c34b1-f774-4ca0-8b31-ebdda1e33f3a" />


---

## ⚙️ Step 2: Configure DNS and Test Records

 On **Server1 DNS Manager**:

   * Ensure **Forward Lookup Zone** `immen.com` exists
   * Add Host (A) records:

     | Name  | IP Address     | Role                 |
     | ----- | -------------- | -------------------- |
     | dc1   | 192.168.99.10  | Primary DC / DNS     |
     | r1    | 192.168.99.254 | Router               |


---

## ⚙️ Step 3: Join Clients to Domain

1. On each client PC:

   * Right-click **This PC → Properties → Change Settings → Domain**
   * Enter domain: `immen.com`
   * Provide domain admin credentials
  

3. Reboot client

<img width="558" height="594" alt="image" src="https://github.com/user-attachments/assets/07d8b292-572b-4788-84e4-cd806fc8cb49" />


4. Verify:

   ```powershell
   whoami
   ping dc1.immen.com
   nslookup dc1.immen.com
   ```

   Expected:

   * `whoami` shows domain user
   * Ping succeeds to Server1
   * DNS resolves `dc1.immen.com`


<img width="1261" height="824" alt="image" src="https://github.com/user-attachments/assets/8b243077-9418-41d2-bfc2-9361ca06f580" />

---



## ⚙️ Step 4: Promote Server2 to Additional Domain Controller (ADC)

1. Open **Server Manager → Add Roles → AD DS**
2. Select **Add a domain controller to an existing domain**

   * Domain: `immen.com`
   * Select **DNS server role** if needed
3. Reboot Server2
4. Verify replication and DNS:

<img width="1558" height="739" alt="image" src="https://github.com/user-attachments/assets/44a585d8-2fbc-4b08-9d32-b2de4c1055ed" />


---

## 🧾 Notes

* DNS role is primarily on Server1, Server2 can act as **secondary** for redundancy
* DHCP remains **on Server1** (VLAN 99)


