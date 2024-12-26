# Active Directory Infrastructure Setup Lab
![image](https://github.com/user-attachments/assets/bbd4ad5d-e99a-49ba-bbec-e38d68f85317)

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
![29](https://github.com/user-attachments/assets/0ab765e8-7ec7-4294-a2e8-67ea750e3b72)
- I logged into the VM and **disabled the Windows Firewall** temporarily to facilitate testing connectivity.
![39](https://github.com/user-attachments/assets/3ba6f242-3958-4926-ae04-c66ddc70442e)

---

### 2. Setup Client-1 in Azure
- I created a **Windows 10 Virtual Machine** named `Client-1` with the following credentials:  
  - **Username:** `labuser`  
  - **Password:** `Cyberlab123!`  
- I ensured that `Client-1` was in the same region and attached to the same **Virtual Network** as `DC-1`.  
- After creating the VM, I configured its **DNS settings** to point to the **Private IP address** of `DC-1`.
![48](https://github.com/user-attachments/assets/92c7b8f3-76be-44c1-a0e5-6fc386072595)
- I restarted `Client-1` from the Azure Portal to apply the DNS settings.  
- I logged into `Client-1` and successfully **pinged DC-1’s private IP address** to confirm network connectivity.
![60](https://github.com/user-attachments/assets/aa4c3d0d-3abf-410b-812b-2a804dbd8477)
- Finally, I opened PowerShell on `Client-1` and ran the command:  
  ```bash
  ipconfig /all

This verified that the DNS settings correctly showed DC-1’s private IP address.
![62](https://github.com/user-attachments/assets/b694d117-ebc6-446f-b3dd-f9f2c8c0fe79)

Notes
- The VMs were left running for future labs. If I wasn’t actively working, I turned off the VMs from the Azure Portal to save costs.
-	This lab is foundational for upcoming labs involving Active Directory configuration and management.
 
