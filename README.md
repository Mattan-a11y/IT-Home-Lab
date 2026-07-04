# IT Home Lab

Home lab where I build and document IT infrastructure from scratch – servers, networking, Active Directory. Each folder is a separate lab with a goal, what I did, problems I hit, and how I fixed them.

---

## Lab 01: Windows Server 2025 Domain Controller

**Goal:** Build a Windows Server and make it a Domain Controller.

**Tools used:**
* VMware
* Windows Server 2025

### What I did
* Installed Windows Server 2025 in VMware.
* Set a static IP address (10.0.0.1).
* Added the Active Directory Domain Services role.
* Promoted the server to a Domain Controller for "lab.local".

### The problem I hit
When I tried to promote the server, I got a red error: the Administrator password was blank.

**How I fixed it:**
Opened PowerShell as Administrator and ran:
`net user Administrator Password123!`
After that, the installation went through.

### Proof
![Server Manager dashboard](01_Active_Directory/01-dashboard.png)
![Static IP configured](01_Active_Directory/01.1-static-ip.png)
![The red error](01_Active_Directory/11-prerequisites-check-error.png)
![Fixed via PowerShell](01_Active_Directory/11.1-prerequisites-check-error.png)
![Active Directory Users and Computers - domain live](01_Active_Directory/13-aduc-done.png)
