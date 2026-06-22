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

## 📸 View Active Directory OU Configuration</summary>
<img width="753" height="528" alt="Screenshot 2026-06-22 at 6 18 11 PM" src="https://github.com/user-attachments/assets/6673ef08-14b3-4722-b810-8530506e10ad" />


*Figure 1: Segmented OU layout supporting isolated security policies for Public Kiosks, Generic Users, and Staff Accounts.*
</details>

---

### 2. Core Server Infrastructure Health
Provisioned and configured the core Windows Server roles required to support network identity and print routing. All services are verified healthy through the consolidated administrative dashboard.

## 📸 View Server Manager Dashboard</summary>
<img width="1088" height="861" alt="Screenshot 2026-06-22 at 6 17 44 PM" src="https://github.com/user-attachments/assets/46ac6bd9-6a04-4cb3-b8b3-0d952abf4985" />

*Figure 2: Server Manager Dashboard validating healthy deployment of AD DS, DNS, and Print Services roles.*
</details>

---

### 3. Client Printer Mapping & Deployment
Simulated a public workstation sending print traffic to the server. Network printers are deployed automatically via GPO preferences, mapping the correct queue based on device location and security group membership.

## 📸 View Workstation Print Mapping</summary>
<img width="1089" height="633" alt="Screenshot 2026-06-22 at 6 17 21 PM" src="https://github.com/user-attachments/assets/067b233f-fab5-4f85-8f29-a855cc92c8c4" />

*Figure 3: Workstation environment verifying access to deployed network queues (`Lib-Public-Kiosk-Printer`).*
</details>

---

### 4. PaperCut NG Secure Release Queue
Integrated PaperCut with the Active Directory user database to intercept incoming jobs. Jobs are held securely in a global virtual queue until authenticated and manually released by the user, preventing data exposure and reducing paper waste.

## 📸 View Secure Release Management Queue</summary>
<img width="1544" height="870" alt="ChatGPT Image Jun 22, 2026, 06_20_31 PM" src="https://github.com/user-attachments/assets/c9155af8-52e4-43ad-96fd-391c0082f7a7" />
*Figure 4: PaperCut NG administrative portal capturing a pending job submitted by a kiosk account.*
</details>

---

### 5. Audit Logging & Cost Tracking
Verified the system's tracking loop by auditing completed, canceled, and modified print requests. Costs are automatically applied based on attributes (grayscale vs. color) to manage budget control guidelines.

## 📸 View Administrative Print Logs</summary>
<img width="1447" height="795" alt="Screenshot 2026-06-22 at 6 16 30 PM" src="https://github.com/user-attachments/assets/cab90152-ee2d-45b5-abc9-a77d46f5565f" />
*Figure 5: Print Job Log database tracking document attributes, submission times, and cost allocations.*
</details>

---

## Key Technical Skills Demonstrated
* **Active Directory Domain Services:** Schema management, OU design, and object grouping.
* **Identity Lifecycle Management:** Synchronizing LDAP/Active Directory objects into third-party application management databases.
* **Print System Engineering:** Deploying network printers, configuring hold/release queues, and implementing cost-accounting rules.
* **System Auditing & Security:** Managing centralized event tracking logs and enforcing secure job releases to safeguard data integrity.
