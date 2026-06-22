# Automated Public Library Print & Identity Infrastructure Lab

## Project Overview
This project simulates a production-ready IT infrastructure designed for a public library system. It integrates Windows Active Directory Domain Services (AD DS) with PaperCut NG to manage user identities, secure print release tracking, and automated client printer deployments. 

The goal of this lab is to enforce secure access baselines, establish logical data segmentation, and control print auditing/quotas across both public kiosks and staff workstations.

---

## Core Infrastructure & Topology
* **Directory Services:** Windows Server 2022 (Active Directory Domain Services & DNS)
* **Print Management:** PaperCut NG (v25.0.11)
* **Print Architecture:** Windows Print Services hosting network-isolated print queues
* **Client Simulation:** Windows 10/11 Enterprise Kiosk profiles

---

## Implementation & Verification Steps

### 1. Active Directory Architecture & Organizational Units
Designed and deployed a customized hierarchical OU structure (`Public-Library-Root`) to separate administrative, staff, guest, and asset objects. This layout ensures precise Group Policy Object (GPO) targeting and secure inheritance boundaries.

<details>
<summary>📸 View Active Directory OU Configuration</summary>
<br>

![Active Directory OU Structure](images/Screenshot%202026-06-22%20at%206.18.11 PM.jpg)

*Figure 1: Segmented OU layout supporting isolated security policies for Public Kiosks, Generic Users, and Staff Accounts.*
</details>

---

### 2. Core Server Infrastructure Health
Provisioned and configured the core Windows Server roles required to support network identity and print routing. All services are verified healthy through the consolidated administrative dashboard.

<details>
<summary>📸 View Server Manager Dashboard</summary>
<br>

![Server Manager Health](images/Screenshot%202026-06-22%20at%206.17.44 PM.jpg)

*Figure 2: Server Manager Dashboard validating healthy deployment of AD DS, DNS, and Print Services roles.*
</details>

---

### 3. Client Printer Mapping & Deployment
Simulated a public workstation sending print traffic to the server. Network printers are deployed automatically via GPO preferences, mapping the correct queue based on device location and security group membership.

<details>
<summary>📸 View Workstation Print Mapping</summary>
<br>

![Client Print Simulation](images/Screenshot%202026-06-22%20at%206.17.21 PM.jpg)

*Figure 3: Workstation environment verifying access to deployed network queues (`Lib-Public-Kiosk-Printer`).*
</details>

---

### 4. PaperCut NG Secure Release Queue
Integrated PaperCut with the Active Directory user database to intercept incoming jobs. Jobs are held securely in a global virtual queue until authenticated and manually released by the user, preventing data exposure and reducing paper waste.

<details>
<summary>📸 View Secure Release Management Queue</summary>
<br>

![PaperCut Jobs Pending Release](images/Screenshot%202026-06-22%20at%206.14.29 PM.jpg)

*Figure 4: PaperCut NG administrative portal capturing a pending job submitted by a kiosk account.*
</details>

---

### 5. Audit Logging & Cost Tracking
Verified the system's tracking loop by auditing completed, canceled, and modified print requests. Costs are automatically applied based on attributes (grayscale vs. color) to manage budget control guidelines.

<details>
<summary>📸 View Administrative Print Logs</summary>
<br>

![PaperCut Print Job Logs](images/Screenshot%202026-06-22%20at%206.16.30 PM.jpg)

*Figure 5: Print Job Log database tracking document attributes, submission times, and cost allocations.*
</details>

---

## Key Technical Skills Demonstrated
* **Active Directory Domain Services:** Schema management, OU design, and object grouping.
* **Identity Lifecycle Management:** Synchronizing LDAP/Active Directory objects into third-party application management databases.
* **Print System Engineering:** Deploying network printers, configuring hold/release queues, and implementing cost-accounting rules.
* **System Auditing & Security:** Managing centralized event tracking logs and enforcing secure job releases to safeguard data integrity.
