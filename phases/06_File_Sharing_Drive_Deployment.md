# 🧾 Active Directory File Sharing & Drive Deployment – Phase 6

## 🎯 Objective

This phase outlines the creation of **departmental shared folders**, **mapped network drives**, and **desktop shortcuts** for users in the *immen.com* domain.
The goal is to provide **secure, easy-to-access file storage** for IT, HR, and Staff teams while maintaining centralized management and access control.

---

## 📂 Folder Structure on File Server

**File server:** `S2`
**Data drive:** `E:\Shares`

```
E:\Shares
├─ IT
│   ├─ Projects
│   ├─ Admin
│   └─ Tools
├─ HR
│   ├─ Payroll
│   ├─ Employee Records
│   └─ Recruitment
└─ Staff
    ├─ General
    ├─ Training
    └─ Reports
```

**Notes:**

* Each top-level folder corresponds to a department.
* Subfolders are used to organize departmental files.
* All folders are located on a **dedicated data drive (E:)** to separate system and data storage.

---

## 🔒 Share Permissions

| Folder | Share Name | Access Control                      |
| ------ | ---------- | ----------------------------------- |
| IT     | IT         | `IT_Domain` (Domain Local Group)    |
| HR     | HR         | `HR_Domain` (Domain Local Group)    |
| Staff  | Staff      | `Staff_Domain` (Domain Local Group) |

**Key Points:**

* **Domain Local groups** control access.
* Permissions are **managed at the top-level folder**; subfolders inherit by default.
* Sensitive subfolders can have **customized additional permissions** if required.

<img width="1274" height="685" alt="image" src="https://github.com/user-attachments/assets/2f729f8b-61ff-43f8-9c68-aa16062cd979" />



---

## 💻 Mapped Network Drives

**GPO Deployment:**

* **Staff:** `Z:` → `\\S2\Shares\Staff`
* **HR:** `Z:` → `\\S2\Shares\HR`
* **IT:** `Z:` → `\\S2\Shares\IT`

**Notes:**

* Drives are mapped using **Group Policy Preferences → Drive Maps**.

---

## 🖥️ Desktop Shortcuts

* Desktop shortcuts are created via **GPO Preferences → Shortcuts**.
* Each shortcut points to the **UNC path** of the department share (e.g., `\\S2\Shares\Staff`) to ensure it works regardless of drive mapping timing.

**Shortcut Details:**

| Department | Shortcut Name | Target Path         |
| ---------- | ------------- | ------------------- |
| Staff      | Staff Drive   | `\\S2\Shares\Staff` |
| HR         | HR Drive      | `\\S2\Shares\HR`    |
| IT         | IT Drive      | `\\S2\Shares\IT`    |

**Benefits:**

* Users can access their departmental files immediately from the desktop.
* Provides intuitive, user-friendly access while enforcing NTFS and share-level permissions.

 <img width="651" height="501" alt="image" src="https://github.com/user-attachments/assets/06cc803c-1390-452f-bbee-8e0356c02d72" />


