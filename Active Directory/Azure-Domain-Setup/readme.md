<h1> ☁️ Setting Up a Domain Environment in Azure </h1>

## ✅ Project Task Summary

- Create a Resource Group 
- Deploy a VNET
- Generate a Domain Controller & Client VM
- Configure VM Settings for Domain use


## 📌 Prerequisites
- 🔐 Microsoft Azure Account (Free or Paid)
- 🌐 Internet connection
- 🧠 Basic understanding of networking concepts (IP, DNS, domain vs workgroup)
  
## 🔗 Enviroments & Technologies Used 
-  **Microsoft Azure**

## 🎥 Video Demonstration

- ### In Progress...

<h1> ⚙️ Project Steps ⚙️ </h1>

## Step 1️⃣: Create a Resource Group  

> 📌 *Why?* A resource group allows you to keep all related Azure resources (VMs, networks, disks, etc.) organized and manageable within a single container.

1. In the **Azure Portal**, go to **Resource Groups**.  
2. Click **+ Create** and name it Azure-DC-Setup.  
3. Choose the correct **region** (Make sure all resources match this region).  
4. Click **Review + Create**, then **Create**.  

<p>
<img src="https://imgur.com/ALp3vCX.png" height="65%" width="65%" alt="RG Creation">
</p>

<br>
<br>

## Step 2️⃣: Create a Virtual Network (VNET)  

> 📌 *Why?* A Virtual Network (VNET) enables secure communication between VMs and other Azure resources, and it's required for setting up domain connectivity between servers and clients.

1. On the Azure Portal, go to **Virtual Networks** & hit create.
2. Ensure the VNET is created under the correct **Resource Group**.  
3. Name the VNET and select the **same region** as your other resources.  
4. Click **Create** to finalize the setup.
 
<p>
<img src="https://imgur.com/rjS0CS4.png" height="50%" width="50%" alt="VNET Creation">
</p>

<br>
<br>

## Step 3️⃣: Create the Domain Controller (DC)  

>📌 *Why?* The Domain Controller is the main server that handles logins, user accounts, and security policies for the entire network.

1. Under the Azure Portal, go to **Virtual Machines** & **Create a Virtual Machine (VM)** under the same **Resource Group**.  
2. Name the VM **Domain-Controller** and ensure it is in the **same region & zone**.  
3. Select the OS version: **Windows Server 2022 Datacenter Hotpatch x64 Gen2**.  
4. Choose a size of **2 vCPUs** (if grayed out, try a different availability zone).
5. **Create login credentials** (For better security, avoid weak passwords and document strong credentials).  
6. ***Navigate*** to **Networking** and **ensure** this VM is on the newly created **VNET**.  
7. Click **Create** to deploy the Domain Controller.  

<p>
<img src="https://imgur.com/K5tdnW3.png" height="20%" width="50%" alt="DC Creation">
</p>

<br>
<br>

## Step 4️⃣: Create the Client VM  

>📌 *Why?* The Client VM is used to test domain connections by acting like a regular user’s computer on the network.

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

## Step 5️⃣: Change Domain Controller's NIC to Static  

> 📌 *Why?* A static IP ensures the Domain Controller is always reachable by clients and services within the network.

1. **Go to the Domain Controller's VM** in the **Azure Portal**.  
2. Click on **Networking** > **Network Settings** & click on the **NIC** at the top (labeled **Network Interface / IP Configuration**).  
3. Click on **ipconfig** and **change the Private IP address setting** from **Dynamic** to **Static**.  
4. Click **Save** to apply the changes.  


<br>

<p>
<img src="https://imgur.com/tec1xN3.png" height="40%" width="50%" alt="NIC Change">
</p>

<br>
<br>

# Step 6️⃣: Change the Client's DNS Server IP to the Domain Controller's Private IP

> 📌 *Why?* Pointing the client’s DNS to the Domain Controller allows proper domain name resolution and enables domain-related services to function correctly.

1. Click on the **Domain Controller's VM** and copy the **Private IP Address** under **Properties**.
2. Go to the **Client's VM** > **Networking** > **Network Settings**.
3. Click on the **NIC** (labeled **Network Interface / IP Configuration**).
4. Under **Settings** > **DNS Servers**, Set **DNS servers** to **Custom** & paste the **Domain Controller's private IP** and **Save**.
5. Restart the **Client's VM** to ensure the NIC settings have been applied.
   

<br>

<p>
<img src="https://imgur.com/Qoz4tqO.png" height="40%" width="50%" alt="DNS IP Change">
</p>
