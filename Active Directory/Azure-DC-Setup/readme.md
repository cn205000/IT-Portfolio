# ☁️ Azure-DC-Setup

### This project walks through setting up a VNET & VM's for a Domain Controller & a client machine in **Microsoft Azure.**
---
## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)


## 📌 Prerequisites
- **Azure subscription** (Free or Paid)
- Access To **RDP**


## 🔗 Enviroments & Technologies Used 
-  **Azure**
- **Remote Desktop Protocol**


---

# *Installation Steps*

# Step 1: Create a Resource Group  

1. In the **Azure Portal**, go to **Resource Groups**.  
2. Click **+ Create** and name it Azure-DC-Setup.  
3. Choose the correct **region** (Make sure all resources match this region).  
4. Click **Review + Create**, then **Create**.  

<p>
<img src="https://imgur.com/ALp3vCX.png" height="65%" width="65%" alt="RG Creation">
</p>

<br>
<br>
<br>
<br>
<br>

# Step 2: Create a Virtual Network (VNET)  

1. On the Azure Portal, go to **Virtual Networks** & hit create.
2. Ensure the VNET is created under the correct **Resource Group**.  
3. Name the VNET and select the **same region** as your other resources.  
4. Click **Create** to finalize the setup.
 
<p>
<img src="https://imgur.com/rjS0CS4.png" height="50%" width="50%" alt="VNET Creation">
</p>

<br>
<br>
<br>
<br>
<br>

# Step 3: Create the Domain Controller (DC)  

1. Under the Azure Portal, go to **Virtual Machines**.
2. **Create a Virtual Machine (VM)** under the same **Resource Group**.  
3. Name the VM **Domain-Controller** and ensure it is in the **same region & zone**.  
4. Select the OS version: **Windows Server 2022 Datacenter Hotpatch x64 Gen2**.  
5. Choose a size of **2 vCPUs** (if grayed out, try a different availability zone).
6. **Create login credentials** (For better security, avoid weak passwords and document strong credentials).  
7. ***Navigate*** to **Networking** and **ensure** this VM is on the newly created **VNET**.  
8. Click **Create** to deploy the Domain Controller.  

<p>
<img src="https://imgur.com/K5tdnW3.png" height="20%" width="50%" alt="DC Creation">
</p>

<br>
<br>
<br>
<br>
<br>

# Step 4: Create the Client VM  

1. **Create a new Virtual Machine (VM)** under the same **Resource Group**.  
2. Name the VM **Client** and ensure it is in the **same region & zone**.  
3. Select the OS version: **Windows 10 Pro 22H2**.  
4. Choose a size of **2 vCPUs** (adjust based on workload).  
5. **Create login credentials** & **check off the licencing box** (For better security, avoid weak passwords and document strong credentials).  
6. Navigate to **Networking** and ensure the VM is on the newly created **VNET**.  
7. Click **Create** to deploy the Client VM.  

<p>
<img src="https://imgur.com/CO3c8ik.png" height="20%" width="50%" alt="Client-VM Creation">
</p>

<br>
<br>
<br>
<br>
<br>

# Step 5: Change Domain Controller's NIC to Static  

1. **Go to the Domain Controller's VM** in the **Azure Portal**.  
2. Click on **Networking** > **Network Settings**.  
3. Click on the **NIC** at the top (labeled **Network Interface / IP Configuration**).  
4. Click on **ipconfig** and **change the Private IP address setting** from **Dynamic** to **Static**.  
5. Click **Save** to apply the changes.  

<p>
<img src="https://imgur.com/tec1xN3.png" height="40%" width="50%" alt="NIC Change">
</p>

<br>
<br>
<br>
<br>
<br>

# Step 6: Change Client's DNS Server IP to Domain Controller's Private IP

1. Click on the **Domain Controller's VM** and copy the **Private IP Address** under **Properties**.
2. Go to the **Client's VM** > **Networking** > **Network Settings**.
3. Click on the **NIC** (labeled **Network Interface / IP Configuration**).
4. Under **Settings** > **DNS Servers**.
5. Click on **DNS servers** and set it to **Custom**, then paste the **Domain Controller's private IP** and click **Save**.
6. Restart the **Client's VM** to ensure the NIC settings have been applied.

<p>
<img src="https://imgur.com/Qoz4tqO.png" height="40%" width="50%" alt="DNS IP Change">
</p>
