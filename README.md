# -Active Directory IAM Lab (User Lifecycle, RBAC &amp; Access Control)

# Windows Server 2025 - Active Directory Domain Services (AD DS) Environment Setup

This repository documents the step-by-step installation, deployment, and hierarchical configuration of a Windows Server 2022 environment. The project showcases the implementation of Active Directory Domain Services (AD DS), core networking roles (DNS, DHCP, IIS, Remote Access), Organizational Unit (OU) design, and Group Policy Management.

---

## 🛠️ Environment Specifications
* **Host Name:** `ECollins-WinSVR`
* **Domain Name:** `ECollins.local`
* **Functional Roles Installed:** AD DS, DNS, DHCP, IIS, File & Storage Services, Remote Access

---

## 🚀 Deployment Phases

### 1. Active Directory Role Installation
The deployment initiated by utilizing the **Add Roles and Features Wizard** within Server Manager to install **Active Directory Domain Services**. This foundational step copies the necessary binaries to the server before promotion.

![AD DS Role Selection](AD%20Install_WinSVR.png)

### 2. Forest Creation & Domain Controller Promotion
Following the binary installation, the server was promoted to a Domain Controller. A new Active Directory forest was provisioned with the root domain name configured as `ECollins.local`.

![Domain Controller Deployment Configuration](Domain_controller_WinSVR.png)

### 3. Post-Deployment Verification & System Authentication
Upon a successful reboot, the system architecture shifted from a local workgroup to a centralized domain environment. The domain functionality is validated via the NetBIOS domain login screen (`ECOLLINS\Administrator`).

![Windows Server Domain Login](WindowsSRV_login.jpg)

Verification through **Active Directory Users and Computers (ADUC)** confirms that the root domain `ECollins.local` is successfully mounted and active.

![Active Directory Domain Verification](Domain_setup_Ecollins.png)

---

## 🏢 Enterprise Infrastructure Layout

### Core Infrastructure Status Dashboard
A centralized look at the Server Manager Dashboard shows a fully operational environment. All core identity and infrastructure services are healthy and running under standard management parameters.

![Server Manager Infrastructure Dashboard](Environment%20Setup.png)

### Organizational Unit (OU) Hierarchy
To mimic a scalable enterprise environment, a geo-distributed Organizational Unit infrastructure was designed. The structure categorizes assets by region and asset type (**Computer**, **Users**, **Server**):

* **ECollins.local**
  * 🇺🇸 **USA** (`Computer`, `Users`, `Server`)
  * 🇪🇺 **Europe** (`Computer`, `Users`, `Server`)
  * 🌏 **Asia** (`Computer`, `Users`, `Server`)
  * 🇦🇺 **Oceania** (`Computer`, `Users`, `Server`)

![Active Directory OU Structure](Organization_Units_Ecollins.png)

### Group Policy Objects (GPO) Management
With the OU infrastructure established, centralized policy enforcement is managed via the **Group Policy Management Console (GPMC)**. Policies such as the `Default Domain Controllers Policy` are linked systematically to enforce security baselines across the respective containers.

![Group Policy Management Console](GPO%20Manager.png)

---

## 🎯 Key Takeaways & Technical Skills
* **Identity & Access Management (IAM):** Provisioning enterprise domain trees/forests and managing directory services.
* **Systems Administration:** Configuring Windows Server core features, handling service dependencies (DNS mapping for AD), and checking server event health.
* **Enterprise Architecture:** Structuring logical administrative boundaries using standard OU inheritance best practices.
