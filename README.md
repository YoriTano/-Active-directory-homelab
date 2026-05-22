# Windows Server 2025 - Enterprise Active Directory & Infrastructure Services Deployment

This repository provides comprehensive documentation for the installation, promotion, and hierarchical engineering of a centralized Windows Server 2022 domain environment. The project showcases industry standard implementation of Active Directory Domain Services (AD DS), fundamental networking roles (DNS, DHCP, IIS, Remote Access), geo-distributed Organizational Unit (OU) structures, and Group Policy management.

---

## 🛠️ System & Environment Specifications

* **Domain Controller Hostname:** `ECollins-WinSVR`
* **Root Domain Name:** `ECollins.local`
* **NetBIOS Domain Name:** `ECOLLINS`
* **Operating System:** Windows Server 2025 Standard
* **Infrastructure Roles:** AD DS, DNS, DHCP, IIS, Remote Access, File & Storage Services

---

## 🚀 Lifecycle & Deployment Phases

### 1. Active Directory Binary Installation
The deployment initiated by utilizing the **Add Roles and Features Wizard** within Server Manager. The **Active Directory Domain Services (AD DS)** role was targeted and selected to install the required baseline binaries onto the local server instance prior to directory promotion.

<img src="AD Install_WinSVR.png" alt="Active Directory Role Selection" width="100%"/>

### 2. Forest Creation & Domain Controller Promotion
Following successful role installation, the server configuration wizard was invoked to elevate the standalone server to a Domain Controller. 

A brand new Active Directory forest was provisioned with the root domain explicitly specified as `ECollins.local`. This process automatically configures the critical underlying DNS service zone dependencies required for domain location services.

<img src="Domain_controller_WinSVR.png" alt="Domain Controller Deployment Configuration" width="100%"/>

### 3. Centralized Environment & Identity Verification
Upon completion of the promotion phase and a mandatory system restart, the local security authority accounts shifted to centralized domain management.

Authentication parameters successfully transition to the directory structure, validated via the network interactive logon interface as `ECOLLINS\Administrator`.

<img src="WindowsSRV_login.jpg" alt="Windows Server Domain Login" width="100%"/>

Post-logon analysis inside **Active Directory Users and Computers (ADUC)** confirms the root partition object `ECollins.local` is fully mounted, active, and responding to directory queries.

<img src="Domain_setup_Ecollins.png" alt="Active Directory Domain Verification" width="100%"/>

---

## 🏢 Enterprise Architecture Implementation

### Core Infrastructure Status Dashboard
A holistic inspection of the **Server Manager Dashboard** displays a completely unified, healthy enterprise environment. All six fundamental system and identity network roles are running within optimal performance thresholds with zero active system management flags.

<img src="Environment Setup.png" alt="Server Manager Infrastructure Dashboard" width="100%"/>

### Geographic Organizational Unit (OU) Design
To model standard multi-regional corporate infrastructure, a structured hierarchy was engineered within the directory. The architecture leverages top-level geographic regions containing nested functional containers to ensure granular administrative delegation and crisp scoping for group policies:

```text
ECollins.local (Root)
├── Builtin
├── Computers
├── Domain Controllers
├── ForeignSecurityPrincipals
├── Managed Service Accounts
├── Users
├── 🇺🇸 USA
│   ├── Computer
│   ├── Users
│   └── Server
├── 🇪🇺 Europe
│   ├── Computer
│   ├── Users
│   └── Server
├── 🌏 Asia
│   ├── Computer
│   ├── Users
│   └── Server
└── 🇦🇺 Oceania
    ├── Computer
    ├── Users
    └── Server
