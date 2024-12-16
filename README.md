# Active Directory Infrastructure Setup Lab

## Overview
In this lab, I prepared the foundational infrastructure for an Active Directory environment using Azure. This included setting up a Domain Controller (DC-1) and a client machine (Client-1) within the same Virtual Network to ensure connectivity and proper configuration.

## Objectives
- Create and configure a Domain Controller (DC-1) with a static private IP address.
- Set up a client machine (Client-1) and ensure it can communicate with the Domain Controller.
- Verify DNS and network connectivity between the two machines.

---

## Steps

### 1. Setup Domain Controller in Azure
- I started by creating a **Resource Group** in the Azure Portal. 
- Next, I created a **Virtual Network** with a Subnet for the lab environment.
- I then deployed a **Windows Server 2022 Virtual Machine** named `DC-1` with the following credentials:  
  - **Username:** `labuser`  
  - **Password:** `Cyberlab123!`  
- After creating the VM, I navigated to its **Network Interface Card (NIC)** settings and set its private IP address to **static**.  
- I logged into the VM and **disabled the Windows Firewall** temporarily to facilitate testing connectivity.

**Screenshot:** Include a screenshot of the NIC settings showing the static private IP address configuration.  
**Screenshot:** Include a screenshot of the firewall settings showing it has been disabled.

---

### 2. Setup Client-1 in Azure
- I created a **Windows 10 Virtual Machine** named `Client-1` with the following credentials:  
  - **Username:** `labuser`  
  - **Password:** `Cyberlab123!`  
- I ensured that `Client-1` was in the same region and attached to the same **Virtual Network** as `DC-1`.  
- After creating the VM, I configured its **DNS settings** to point to the **Private IP address** of `DC-1`.  
- I restarted `Client-1` from the Azure Portal to apply the DNS settings.  
- I logged into `Client-1` and successfully **pinged DC-1’s private IP address** to confirm network connectivity.  
- Finally, I opened PowerShell on `Client-1` and ran the command:  
  ```bash
  ipconfig /all

This verified that the DNS settings correctly showed DC-1’s private IP address.

Screenshot: Include a screenshot of the DNS settings configuration in Client-1.
Screenshot: Include a screenshot of the successful ping result from Client-1 to DC-1.
Screenshot: Include a screenshot of the PowerShell output showing the DNS settings in Client-1.

Notes
- The VMs were left running for future labs. If I wasn’t actively working, I turned off the VMs from the Azure Portal to save costs.
-	This lab is foundational for upcoming labs involving Active Directory configuration and management.
 
