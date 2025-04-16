<h1> Traffic Monitoring Between Two Azure VMs with Wireshark </h1>

## ✅ Project Task Summary

- [ ] Create a Resource Group 
- [ ] Deploy a VNET
- [ ] Generating a Domain Controller & Client VM
- [ ] Configuring VM Settings for Domain use


## 📌 Prerequisites
- 🔐 Microsoft Azure Account (Free or Paid)
- 🌐 Internet connection
- ✅ Have gone through & finished the previous project in the repository.
- 💻 **Remote Desktop Protocol (RDP)** access.
- 🧠 Basic Understanding of:
  - ICMP protocol and ping functionality
  - **Network Security Groups (NSGs)**
  
## 🔗 Enviroments & Technologies Used 
-  **Microsoft Azure**
-  **Windows 10 Pro VM**
-  **Linux VM (ubuntu 22.04)**
-  **Remote Desktop Protocol**
-  **Wireshark**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>

## Step 1️⃣: Using Remote Desktop Protocol (RDP)

1. In Azure, open your **Windows VM** and copy its **Public IP Address**.
2. On your local machine, search for and open **Remote Desktop Connection**.
3. Paste the copied IP into the **Computer** field.
4. Enter the **Windows VM username**, click **Connect**, and log in.


<p>
<img src="https://imgur.com/JclDJbE.png" height="90%" width="90%" alt="RDP">
</p>

<br>
<br>

## Step 2️⃣: Installing Wireshark on Windows VM 

1. After connecting to the **Windows VM**, open **Microsoft Edge**.
2. Go to: www.wireshark.org/#downloadLink
3. Download the **Windows x64 Installer**, launch it, and install using the default settings.

<p>
<img src="https://imgur.com/VAInGnm.png" height="90%" width="90%" alt="Wireshark Installation">
</p>

<br>
<br>

## Step 3️⃣: Capturing ICMP Traffic in Wireshark

1. On the **Windows VM**, open **Wireshark** via the Start menu.
2. Select the **Ethernet interface**, then in the filter bar type: icmp & press **Enter** to apply the filter.
3. In Azure, locate your **Linux VM** and copy its **Private IP address**.
4. Back on the **Windows VM**, open **PowerShell** and run: ping <Linux Private IP>
5. You should immediately see ICMP ping traffic appear in **Wireshark**.


<p>
<img src="https://imgur.com/A7yqmNX.png" height="70%" width="70%" alt="Pinging LinuxVM">
</p>

<br>
<br>

## Step 4️⃣: Block ICMP Traffic Using NSG Rules

1.  On the **Windows VM**, run a continuous ping to the **Linux VM** using: ping <Linux Private IP> -t
2. In Azure, go to the **Linux VM** > **Networking** > **Network Settings**.
3. Under *Essentials*, click on the **Network Security Group (NSG)**.
4. Navigate to **Settings** > **Inbound Security Rules** → Click **Add**.
5. Set the following values:  
  - **Destination Port Ranges**: `*`  
  - **Protocol**: `ICMP`  
  - **Action**: `Deny`  
  - **Priority**: `290`  
  → Then click **Add**.
6. Return to the **Windows VM** and observe that the ping requests should begin timing out.
7. Once verified, return to the **Linux VM** NSG and **delete the ICMP Deny rule** to restore connectivity.
8. On Powershell, press **Ctrl + C** to stop the pereptual ping.

<p>
<img src="https://imgur.com/vzhjzj9.png" height="80%" width="80%" alt="Blocking ICMP Traffic">
</p>

<br>
<br>

## Step 5️⃣: Observing SSH Traffic

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

1. Click on the **Domain Controller's VM** and copy the **Private IP Address** under **Properties**.
2. Go to the **Client's VM** > **Networking** > **Network Settings**.
3. Click on the **NIC** (labeled **Network Interface / IP Configuration**).
4. Under **Settings** > **DNS Servers**, Set **DNS servers** to **Custom** & paste the **Domain Controller's private IP** and **Save**.
5. Restart the **Client's VM** to ensure the NIC settings have been applied.
   

<br>

<p>
<img src="https://imgur.com/Qoz4tqO.png" height="40%" width="50%" alt="DNS IP Change">
</p>

