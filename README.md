# Active Directory IAM Lab (User Lifecycle, RBAC & Access Control)
This repository provides comprehensive documentation for the installation, promotion, and hierarchical engineering of a centralized Windows Server 2025 domain environment. The project showcases industry-standard implementation of Active Directory Domain Services (AD DS), fundamental networking roles (DNS, DHCP, IIS, Remote Access), geo-distributed Organizational Unit (OU) structures, and Group Policy management.

---

## 🛠️ System & Environment Specifications

* **Domain Controller Hostname:** `ECollins-WinSVR`
* **Root Domain Name:** `ECollins.local`
* **NetBIOS Domain Name:** `ECOLLINS`
* **Operating System:** Windows Server 2025 Standard
* **Infrastructure Roles:** AD DS, DNS, DHCP, IIS, Remote Access, File & Storage Services

---

# Active Directory IAM Lab (User Lifecycle, RBAC & Access Control)

This project demonstrates hands-on Identity and Access Management (IAM) using an Active Directory homelab.

It simulates real-world IAM processes including:
* **User provisioning** (Joiner)
* **Role-based access control** (RBAC)
* **Role changes** (Mover)
* **Access validation**
* **User deprovisioning** (Leaver)
* **File/folder access control**

---

## 🔹 Environment Setup

A Windows Server domain controller was configured with Active Directory Domain Services (AD DS), DNS, DHCP, IIS, and Remote Access roles using the Server Manager Wizard.
### Server Dashboard
<img width="1714" height="920" alt="Environment Setup" src="https://github.com/user-attachments/assets/ce106e73-a432-4e96-a699-df0ccd2e6a3e" />


### Active Directory Installation
<img width="1716" height="919" alt="AD Install_WinSVR" src="https://github.com/user-attachments/assets/857535f5-3e58-4a03-9032-36c64f011cf2" />


### Domain Controller Login
<img width="761" height="553" alt="Domain_controller_WinSVR" src="https://github.com/user-attachments/assets/bc27ebca-b4b0-4f01-aba1-d9f809a728c0" />

### Domain Controller Setup
<img width="1715" height="434" alt="Domain_setup_Ecollins" src="https://github.com/user-attachments/assets/bccddf34-7394-4f50-8426-d1b32c6328f0" />


### Server Infrastructure Dashboard

---

## 🔹 Domain & OU Structure

The domain `ECollins.local` was successfully initialized. To mimic a production corporate environment, a top-level geo-distributed Organizational Unit (OU) design was implemented, splitting objects into specific regional tiers:

* **USA** (`Computer`, `Server`, `Users`)
* **Europe** (`Computer`, `Server`, `Users`)
* **Asia** (`Computer`, `Server`, `Users`)
* **Oceania** (`Computer`, `Server`, `Users`)
* **Disabled Users** (Dedicated container for lifecycle management)

### OU Structural Design
<img width="1714" height="550" alt="Organization_Units_Ecollins" src="https://github.com/user-attachments/assets/5afc087a-315f-4a99-90d6-6278aa4f5a81" />

---

## 🔹 Security Groups & Distribution Lists

Security groups and distribution lists were provisioned to establish strict Role-Based Access Control (RBAC) boundaries and structured communication channels across the forest:

| Group Name | Group Type | Scope | Purpose |
| :--- | :--- | :--- | :--- |
| **IT_Admin** | Security Group | Global | Administrative access control and tier management |
| **HR_Group** | Security Group | Global | Human Resources data boundaries |
| **Financial_Read** | Security Group | Global | Read-only access to financial shared infrastructure |
| **DL-AllEmployees** | Distribution | Global | Organization-wide email distribution array |
| **DL-ITAdmins** | Distribution | Global | Departmental IT-specific distribution array |

### Role-Based Security Groups(RBAC Foundation)
<img width="852" height="526" alt="Security_Group_DL" src="https://github.com/user-attachments/assets/810da536-e83b-4815-9885-572fd8dc6e1c" />

---
---
##  🔹User Provisoning (Joiner)
New users were created and placed into the correct OU based on department

### User Provisioning
<img width="745" height="428" alt="Joiner_AD" src="https://github.com/user-attachments/assets/bcadbe6e-c957-407e-96c2-4228f0b50b31" />

---
## User Deprovisoning (Leaver)

User account disabled and moved to a “Disabled Users” OU to remove access.

### Account Disabled
<img width="588" height="341" alt="Leaver_AD" src="https://github.com/user-attachments/assets/e16a35b2-b1dc-4e6c-9d91-611e75d43d71" />




## 🔹 Group Policy Object (GPO) Management

To enforce structural security baselines, a clear separation of policies was established between domain-wide scopes and dedicated domain controller configurations. 

* **Default Domain Policy:** Configured for high-level enforcement (e.g., global password complexity, lockout thresholds).
* **Default Domain Controllers Policy:** Linked directly to the Domain Controllers container to restrict local administrative rights and audits.

### Group Policy Management Console
<img width="1670" height="913" alt="GPO Manager" src="https://github.com/user-attachments/assets/d81b51f9-be35-4424-a202-f9e622ca6449" />


---

## 🔹 Key IAM Concepts Practiced

* **User Lifecycle Management:** Modeling the full lifecycle timeline of enterprise corporate identities (Joiner, Mover, Leaver).
* **Role-Based Access Control (RBAC):** Binding data access permissions strictly to directory groups rather than explicit individual accounts.
* **Principle of Least Privilege (PoLP):** Ensuring visibility restrictions (such as `Financial_Read`) limit high-risk surface areas to absolute necessity.
* **Directory Structural Design:** Planning nested OU pathways that maximize inheritance predictability and simplify targeted GPO linking.

---

## 🔹 Tools Utilized

* **Active Directory Domain Services (AD DS)**
* **Active Directory Users and Computers (ADUC)**
* **Group Policy Management Console (GPMC)**
* **Windows Server 2025 Ecosystem**
