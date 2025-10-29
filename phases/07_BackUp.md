# **Phase 7: Backup Implementation**

## **1. Objective**

The goal of this phase is to ensure **availability and recoverability** of critical services and data in the Active Directory environment. Specifically:

* Protecting Active Directory (AD) database and system settings
* Securing shared folder data on the file server
* Establishing a backup strategy for disaster recovery

---

## **2. Environment Overview**

| Server | Role                                                     | Backup Type                                     | Notes                                              |
| ------ | -------------------------------------------------------- | ----------------------------------------------- | -------------------------------------------------- |
| **S1** | Primary Domain Controller (PDC) – FSMO holder, DNS, DHCP | System State (separate backup)                  | Protects AD database, registry, SYSVOL             |
| **S2** | Additional Domain Controller (ADC) + File Server         | System State + Shared Folders (combined backup) | Provides redundancy for AD and backup of user data |

---

## **3. Backup Details (GUI-Based)**

### **3.1 System State Backup (S1)**

**Purpose:**

* Protect Active Directory database (`NTDS.dit`), SYSVOL, registry, and boot files
* Preserve domain configuration and DNS/DHCP settings

**Steps (GUI):**

1. Open **Server Manager → Tools → Windows Server Backup**
2. Click **Local Backup → Backup Once**
3. Choose **Custom → Add Items → System State**
4. Select **backup destination**
5. Click **Backup** and monitor progress
6. Confirm completion

**Result:**

* S1 system state backup completed successfully

<img width="848" height="735" alt="image" src="https://github.com/user-attachments/assets/b2d1a9e8-325a-4101-8dca-f41d315625ab" />



---

### **3.2 Combined System State + Shared Folders Backup (S2)**

**Purpose:**

* Protect Active Directory redundancy (System State)
* Backup all shared folders 

**Steps (GUI):**

1. Open **Windows Server Backup → Backup Once**
2. Choose **Custom → Add Items**
3. Select **System State** and **shared folder paths** simultaneously
4. Select **backup destination** 
5. Click **Backup** and monitor progress
6. Confirm completion

**Result:**

* S2 backup includes both System State and shared folders in a single job
* Simplifies backup management and ensures both AD and file data are protected

<img width="1044" height="571" alt="image" src="https://github.com/user-attachments/assets/2d2e73ee-208a-4426-8921-2e3b6f3d58eb" />

---

## **4. Verification**


* Check backup history in **Windows Server Backup → Local Backup → Backup History**
* Verify log files at:

  ```
  C:\Windows\Logs\WindowsServerBackup

  ```

<img width="857" height="148" alt="image" src="https://github.com/user-attachments/assets/f240ac0f-58f2-4aea-ada5-2cf5fcc764dd" />

---

Phase 7 ensures **business continuity** through proper backup of both Active Directory and user data. By using the **GUI**, the workflow is clear and straightforward:

* **S1:** System State backup (separate)
* **S2:** Combined System State + shared folders backup

This approach provides redundancy, data protection, and a foundation for disaster recovery.


