# ☁️ Azure-DC-Setup

### This project walks through setting up a VNET & VM's for a Domain Controller & a client machine in **Microsoft Azure.**
---
## Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)


## 📌 Prerequisites
- **Azure subscription** (Free or Paid)
- Access To **RDP**


## 🔗 Enviroments & Technologies Used 
-  **Azure**
- **Remote Desktop Protocol**


---

<h1>Installation Steps</h1>

## Step 1: Create a Resource Group  

1. In the **Azure Portal**, go to **Resource Groups**.  
2. Click **+ Create** and name it `Azure-DC-Setup`.  
3. Choose the correct **region** (Make sure all resources match this region).  
4. Click **Review + Create**, then **Create**.  

<p>
<img src="https://imgur.com/ALp3vCX.png" height="65%" width="65%" alt="RG Creation">
</p>



## Step 2: Create a Virtual Network (VNET)  

1. On the Azure Portal, go to **Virtual Networks** & hit create.
2. Ensure the VNET is created under the correct **Resource Group**.  
3. Name the VNET and select the **same region** as your other resources.  
4. Click **Create** to finalize the setup.
 
<p>
<img src="https://imgur.com/rjS0CS4.png" height="50%" width="50%" alt="VNET Creation">
</p>



## Step 3: Create the Domain Controller (DC)  

1. Under the Azure Portal, go to **Virtual Machines**.
2. **Create a Virtual Machine (VM)** under the same **Resource Group**.  
3. Name the VM **Domain-Controller** and ensure it is in the **same region & zone**.  
4. Select the OS version: **Windows Server Datacenter 2022 Hotpatch**.  
5. Choose a size of **2 vCPUs** (if grayed out, try a different availability zone).
6. **Create login credentials** (For better security, avoid weak passwords and document strong credentials).  
7. ***Navigate*** to **Networking** and **ensure** this VM is on the newly created **VNET**.  
8. Click **Create** to deploy the Domain Controller.  

<p>
<img src="https://imgur.com/K5tdnW3.png" height="20%" width="50%" alt="VNET Creation">
</p>

