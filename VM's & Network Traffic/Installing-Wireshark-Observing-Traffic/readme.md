<h1>  🧪 Observing ICMP Traffic Between VMs </h1>

## ✅ Project Task Summary

- [ ] Create a Resource Group 
- [ ] Deploy a VNET
- [ ] Generating a Domain Controller & Client VM
- [ ] Configuring VM Settings for Domain use


## 📌 Prerequisites
- 🔐 Microsoft Azure Account (Free or Paid)
- 🌐 Internet connection
- 🧠 Basic understanding of networking concepts (IP, DNS, domain vs workgroup)
  
## 🔗 Enviroments & Technologies Used 
-  **Microsoft Azure**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>

## ‼️ *Prerequsite Steps* ‼️

### Step 1️⃣: Using Remote Desktop 
1. Windows search for **Remote Desktop Connection** to connect to your **Windows 10 Virtual Machine**.
2. Under *Computer*, put in the **Windows 10 Virtual Machine IP Address**.
3. Connect & input your Windows 10 VM **Account Info**



### Step 2️⃣: Install Wireshark on Windows VM  
1. Within your **Windows 10 VM**, go to **Microsoft Edge** then download and install **Windows X64 Installer** from *wireshark.org/download.html*  
2. Go through the Wizard, clickin *Next* & *Install* until the wizard is finished.
3. Launch **Wireshark** & click on **Ethernet** to begin a session.






### Step 3️⃣: Filter for ICMP Traffic  
1. In Wireshark, use the filter box and type:  
