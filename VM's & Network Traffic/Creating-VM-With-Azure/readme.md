<h1> 🌐 Setting Up Windows & Linux Virtual Machines in the Same Network </h1>

## ✅ Project Task Summary

- [ ] Creating a Resource Group 
- [ ] Generating a Windows & Linux VM


## 📌 Prerequisites
- 🔐 Microsoft Azure Account (Free or Paid)
- 🌐 Internet connection
- 🧠 Basic understanding of networking concepts
  
## 🔗 Enviroments & Technologies Used 
-  **Microsoft Azure**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>


## Step 1️⃣: Create a Resource Group  
1. In the Azure Portal, navigate to **Resource Groups**.  
2. Click **Create**, enter a name, choose a region, then click **Review + Create** → **Create**.

<br>

## Step 2️⃣: Create a Windows 10 Virtual Machine (VM)  
1. Go to **Virtual Machines** in Azure and click **Create** → **Azure Virtual Machine**.  
2. Under the **Basics** tab:  
   - Select the **previously created Resource Group**.
   - Pick the same **Region** for the **previously created Resource Group**.
   - Choose **Windows 10 Pro** for the image.  
3. In the **Networking** tab:  
   - Note the **Virtual Network (VNET)** and **Subnet** that's automatically created.  
4. Complete the configuration and click **Review + Create** → **Create**.

<br>

## Step 3️⃣: Create a Linux (Ubuntu) Virtual Machine (VM)  
1. Go to **Virtual Machines** and click **Create** → **Azure Virtual Machine**.  
2. Under the **Basics** tab:  
   - Select the **same Resource Group** used earlier.
   - Pick the same **Region** for the **previously created Resource Group**.
   - Choose **Ubuntu Server 22.04 LTS x64** for the image.  
   - Set **Authentication type** to **Username/Password**.  
3. In the **Networking** tab:  
   - Select the **same Virtual Network and Subnet** used by the Windows VM.  
4. Complete the configuration and click **Review + Create** → **Create**.

<br>
