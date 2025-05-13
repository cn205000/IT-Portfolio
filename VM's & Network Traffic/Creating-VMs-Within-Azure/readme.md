<h1> 🌐 Setting Up Windows & Linux Virtual Machines in the Same Network </h1>

## ✅ Project Task Summary

- Create a Resource Group in Azure  
- Deploy both Windows and Linux Virtual Machines  
- Connect both VMs to the same Virtual Network for seamless communication  

## 📌 Prerequisites

- 🔐 Microsoft Azure Account (Free or Paid)  
- 🌐 Stable internet connection  
- 🧠 Basic understanding of virtual machines and networking  

## 🔗 Environments & Technologies Used 

- **Microsoft Azure**  
- **Windows 10 Pro VM**  
- **Ubuntu Server 22.04 VM**  

# 🎥 Video Demonstration

- ## [Video Tutorial](https://vimeo.com/1084040215/bfe15f16ea?share=copy)
  
<h1> ⚙️ Project Steps ⚙️ </h1>


## Step 1️⃣: Create a Resource Group  

>📌 *Why?* A Resource Group helps organize and manage all the related resources for your project in one place.

1. In the Azure Portal, navigate to **Resource Groups**.  
2. Click **Create**, enter a name, choose a region, then click **Review + Create** → **Create**.

<p>
<img src="https://imgur.com/DXPxCjA.png" height="35%" width="35%" alt="RG Creation">
</p>

<br>

## Step 2️⃣: Create a Windows 10 Virtual Machine (VM)  

>📌 *Why?* This VM will act as the client system for testing connections and monitoring network traffic.

1. Go to **Virtual Machines** in Azure and click **Create** → **Azure Virtual Machine**.  
2. Under the **Basics** tab:  
   - Select the **previously created Resource Group**.
   - Pick the same **Region** for the **previously created Resource Group**.
   - Choose **Windows 10 Pro** for the image.  
3. In the **Networking** tab:  
   - Create new **Virtual Network** & name it. 
4. Complete the configuration and click **Review + Create** → **Create**.
   (Wait for the VNET to be created before next step.)

<p>
<img src="https://imgur.com/HFnUwht.png" height="40%" width="40%" alt="Windows Creation">
</p>

<br>

## Step 3️⃣: Create a Linux (Ubuntu) Virtual Machine (VM)  

>📌 *Why?* The Linux VM acts as the second system in the network, allowing you to simulate communication between two machines.

1. Go to **Virtual Machines** and click **Create** → **Azure Virtual Machine**.  
2. Under the **Basics** tab:  
   - Select the **same Resource Group** used earlier.
   - Pick the same **Region** for the **previously created Resource Group**.
   - Choose **Ubuntu Server 22.04 LTS x64** for the image.  
   - Set **Authentication type** to **Username/Password**.  
3. In the **Networking** tab:  
   - Select the **same Virtual Network** used by the Windows VM.  
4. Complete the configuration and click **Review + Create** → **Create**.

<p>
<img src="https://imgur.com/NzJ71jA.png" height="40%" width="40%" alt="Linux Creation">
</p>

<br>
