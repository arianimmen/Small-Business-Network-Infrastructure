# 🧾 Group Policy Documentation – Phase 4

## 🎯 Objective

This document outlines the Group Policy configuration for the **IT (Admins)**, **Staff**, and **HR** Organizational Units (OUs) in the *immen.com* domain.
The goal is to provide a secure and well-structured environment where IT administrators have full control, Staff users have a restricted desktop, and HR users have the same restrictions as Staff but with access to HR specific resources.

---

## 🧑‍💻 IT Department (Admins)

**GPO Name:** `IT-Group Policy`
**Linked OU:** `immen.com/IT`

### **Configured Policies**

| Category                        | Setting   | Description                                                                   |
| ------------------------------- | --------- | ----------------------------------------------------------------------------- |
| **Control Panel**               | ✅ Allowed | IT can open, configure, and view all system settings.                         |
| **CMD / PowerShell / Registry** | ✅ Allowed | Required for troubleshooting, scripting, and configuration.                   |
| **Network Settings**            | ✅ Allowed | IT can change IP addresses, DNS settings, and network adapter configurations. |

### **Purpose**

Provide administrators with full local control of system settings to maintain and manage networked computers efficiently.

---

## 👨‍💼 Staff Department

**GPO Name:** `Staff-Group Policy`
**Linked OU:** `immen.com/Staff`

### **Configured Policies**

| Category                   | Setting                        | Description                                                 |
| -------------------------- | ------------------------------ | ----------------------------------------------------------- |
| **Control Panel**          | 🚫 Disabled                    | Users cannot open or modify system settings.                |
| **CMD / Registry**         | 🚫 Disabled                    | Command prompt and registry access are restricted.          |
| **Network Settings**       | 🚫 Disabled                    | Prevents users from changing IP or network configurations.  |
| **Wallpaper**              | ✅ Enforced (e.g. company logo) | Ensures a unified desktop background for all staff members. |
| **Account Lockout Policy** | ✅ Normal                       | Standard domain security policy applies.                    |

### **Purpose**

Restrict system-level access to prevent unauthorized configuration changes and maintain consistency across user desktops.

---

## 🧑‍💼 HR Department

**GPO Name:** `HR_StandardDesktop`
**Linked OU:** `immen.com/HR`

### **Configured Policies**

| Category                   | Setting                                          | Description                                                                    |
| -------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------ |
| **Control Panel**          | 🚫 Disabled                                      | HR staff cannot open or modify system settings.                                |
| **CMD / Registry**         | 🚫 Disabled                                      | Command prompt and registry access are restricted to prevent system tampering. |
| **Network Settings**       | 🚫 Disabled                                      | Users cannot modify IP or DNS configurations.                                  |
| **Wallpaper**              | ✅ Enforced (e.g., HR logo or company background) | Ensures consistent appearance across HR computers.                             |
| **Account Lockout Policy** | ✅ Normal                       | Standard domain security policy applies.                    |



