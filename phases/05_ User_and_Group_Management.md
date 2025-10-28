#  Active Directory User and Group Management – Phase 5

## 🎯 Objective

This document outlines the process for **creating users in Active Directory** and **adding them to the correct groups** for role-based access management in the *immen.com* domain.
The goal is to maintain a **secure, organized, and scalable environment** where department users inherit permissions automatically via **Global and Domain Local groups**.

---
## User Creation

Users were created by a script using csv. You can check the Script in the conf file.

## 🏷️ Group Creation

**OU for Groups:** `OU=Groups,DC=immen,DC=com`

* **Global Groups:** Contain all users from a single department.

  * `IT_Global`
  * `HR_Global`
  * `Staff_Global`
* **Domain Local Groups:** Assigned to resources within the domain.

  * `IT_Domain`
  * `HR_Domain`
  * `Staff_Domain`

**Purpose:**

* **Global groups** represent roles or departments.
* **Domain Local groups** represent **resource access** (shared drives, printers, applications).
* Users gain permissions indirectly via Global → Domain Local group nesting (**AGDLP best practice**).

<img width="1174" height="864" alt="image" src="https://github.com/user-attachments/assets/f6211652-6721-4f01-adfd-2c5de7537255" />


