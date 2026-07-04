# Lab 01: Windows Server 2025 Domain Controller

**Goal:** Build a Windows Server and make it a Domain Controller.

**Tools used:**
* VMware
* Windows Server 2025

## What I did:
* Installed Windows Server 2025 in VMware.
* Set a static IP address (10.0.0.1).
* Added the Active Directory Domain Services role.
* Promoted the server to a Domain Controller for "lab.local".

## The Problem I Hit:
When I tried to promote the server, I got a big red error. 
The error said the Administrator password was blank. 

**How I fixed it:**
I opened PowerShell as Administrator and typed:
`net user Administrator Password123!`
After that, the installation worked perfectly.

## Proof:
![Server Manager](01-dashboard.png)
![Static IP](04-static-ip.png)
![The Red Error](11-prerequisites-check-error.png)
![Active Directory Users](13-aduc-done.png)
```
