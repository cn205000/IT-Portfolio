<h1> 🛠️ Configuring a Domain Controller & Active Directory </h1>

## ✅ Project Task Summary

- Connect to VMs Using RDP
- Configure the Domain Controller within the Virtual Windows Server Machine
- Disable Domain Firewall & Test Connection to Domain Controller
- Configure Client VM Settings for Domain use

## 📌 Prerequisites
- 🌐 Internet connection
- 🧠 Basic understanding of networking concepts (IP, DNS, domain vs workgroup)
- 💻 Windows Machine with Remote Desktop Protocol (RDP) installed (most have it by default)
- 🔐 Microsoft Azure Account (Free or Paid)
- 🔧 Have a Resource Group, Virtual Network, & Virtual Machines created (via previous project)
- ✅ Completed The Creation Of Azure Network Environment  (Previous Project) 
    
## 🔗 Enviroments & Technologies Used 
-  Microsoft Azure
-  2022 Windows Server
-  Windows 10 Pro
-  Remote Desktop Protocol
-  Command Prompt
-  Windows Server Manager

  ## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>

## Step 1️⃣: Using Remote Desktop Protocol (RDP)

>📌 *Why?* RDP lets you securely connect and control your Domain Controller from your local computer.

1. Go to your **Domain Controller VM** on Azure and copy the **Public IP Address**.
2. On the Windows search bar, search for **Remote Desktop Connection** and open it.
3. Paste the IP into the box labeled **Computer**.
4. Enter the **username and password** you configured for the Domain Controller VM, **Connect** and login.

<p>
<img src="https://imgur.com/hE04qpk.png" height="75%" width="75%" alt="RDP">
</p>

<br>
<br>

## Step 2️⃣: Configuring the Domain Controller (DC)

>📌 *Why?* This turns the server into a Domain Controller, which manages users, computers, and domain security for the network.

1. On the DC VM, open **Server Manager**.
2. Click **Add Roles & Features** > Next > Next > Next.
3. Select **Active Directory Domain Services**, click Next until you reach **Install**.
4. Check **Restart destination server automatically** and click **Install**.
5. After installation, click the **flag icon** in Server Manager > **Promote this server to a domain controller**.
6. Choose **Add a new forest** and create a domain (e.g., mydomain.com), then click Next.
7. For the **Directory Services Restore Mode (DSRM)** password, set anything (easy password for testing purposes).
8. Uncheck **Create DNS delegation** when prompted & continue through the wizard and click **Install**.
9. Once the server restarts, log in via **domain credentials**: domain\Username. (eg. mydomain.com\admin123)
 
<p>
<img src="https://imgur.com/HyyWl3h.png" height="85%" width="85%" alt="Server Manager">
</p>

<br>
<br>

## Step 3️⃣: Disable Firewall on DC (for testing/ping)

>📌 *Why?* Disabling the firewall allows easier network testing, like pings during setup (not recommended for production).

1. Open Run in Windows search, type wf.msc, and press Enter.
2. Click **Windows Firewall Properties** (top of the left panel).
3. For **Domain, Private, and Public Profiles**, set **Firewall State** to **Off**.
4. Click **Apply** and **OK**.

<p>
<img src="https://imgur.com/Nl9jiWR.png" height="80%" width="80%" alt="Firewall">
</p>

<br>
<br>

## Step 4️⃣: Test Connection from Client VM

>📌 *Why?* Verifying DNS and ping ensures the Client VM can communicate with the DC before trying to join the domain.


RESTART DC FIRST

1. Open Azure & navigate to your **Domain Controller**. Restart the VM to ensure the Firewall settings have been set.
2. RDP into your **Client VM**. (We are not using domain login yet as this client hasn't joined the domain yet).
3. Open **PowerShell** and run:  
   ping <DC_Private_IP> (We should see that all packets were sent and received).
4. Run:  
   ipconfig /all
 (Look for "DNS Server"; it should be linked to the DC's private IP)


<p>
<img src="https://imgur.com/nx5nKxs.png" height="40%" width="70%" alt="Command Prompt">
</p>

<br>
<br>

## Step 5️⃣: Join Client VM to Domain

>📌 *Why?* Joining the domain connects the client to the centralized management system handled by the Domain Controller.

1. On the **Client VM** open **System Properties** (type 'Run' then sysdm.cpl).
2. Click **Change**, select **Domain**, and enter the domain name you set earlier (e.g., mydomain.com).
3. When prompted, enter **Domain Admin credentials** (the ones set during DC configuration).
4. After confirmation, **restart the Client VM**. On reboot, log in using mydomain.com\YourUser.

<p>
<img src="https://imgur.com/EKHU4I2.png" height="80%" width="80%" alt="Joining Domain via Client VM">
</p>

<br>
<br>

## Step 6️⃣: Allow Domain Users to Use RDP

>📌 *Why?* This lets regular domain users connect to the Client VM via Remote Desktop after joining the domain.

1. Reconnect to the **Client VM** using the **DC admin account**.
2. Open **System Properties** (type 'Run' then sysdm.cpl)
3. Under **Remote**, click **Select Users** then **Add**, type **domain users** then Apply and save changes.
   
<p>
<img src="https://imgur.com/NMBAGxU.png" height="80%" width="80%" alt="Adjusting GP">
</p>
