# 🛠️ Configuring a Domain Controller & Active Directory

## ✅ Project Task Summary

- [ ] Connecting to VMs Using RDP
- [ ] Configuring the Domain Controller within the Virtual Windows Server Machine
- [ ] Disabling Firewall & Testing Connection to Domain Controller
- [ ] Configuring Client VM Settings for Domain use

## 📌 Prerequisites
- 🌐 Internet connection

- 🧠 Basic understanding of networking concepts (IP, DNS, domain vs workgroup)

- 💻 Windows Machine with Remote Desktop Protocol (RDP) installed (most have it by default)

- 🔐 Microsoft Azure Account (Free or Paid)

- 🔧 Have a Resource Group, Virtual Network and Virtual Machines created (via previous project) 
    
## 🔗 Enviroments & Technologies Used 
-  Microsoft Azure
-  2022 Windows Server
-  Windows 10 Pro
-  Remote Desktop Protocol
-  Command Prompt
-  Windows Server Manager

  ## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

# *Installation Steps*

## Step 1: 🔐 Using Remote Desktop Protocol (RDP)

1. Go to your **Domain Controller VM** on Azure and copy the **Public IP Address**.
2. On your Windows search bar, search for **Remote Desktop Connection** and open it.
3. Paste the IP into the box labeled **Computer**.
4. Enter the **username and password** you configured for the Domain Controller VM.
5. Click **Connect** and login.

<p>
<img src="https://imgur.com/hE04qpk.png" height="75%" width="75%" alt="RDP">
</p>

<br>
<br>
<br>

## Step 2. 🏗️ Configuring the Domain Controller (DC)

1. On the DC VM, open **Server Manager**.
2. Click **Add Roles & Features** > Next > Next > Next.
3. Select **Active Directory Domain Services**, click Next until you reach **Install**.
4. Check **Restart destination server automatically** and click **Install**.
5. After installation, click the **flag icon** in Server Manager > **Promote this server to a domain controller**.
6. Choose **Add a new forest** and create a domain (e.g., `mydomain.com`), then click Next.
7. For the **Directory Services Restore Mode (DSRM)** password, set anything strong or easy if for testing purposes.
8. Uncheck **Create DNS delegation** when prompted.
9. Continue through the wizard and click **Install**.
10. Once the server restarts, you must now log in via **domain credentials**: `domain\Username`. (eg. mydomain.com\admin123)
 
<p>
<img src="https://imgur.com/HyyWl3h.png" height="85%" width="85%" alt="Server Manager">
</p>

<br>
<br>
<br>

## Step 3: 🔥 Disable Firewall on DC (for testing/ping)

1. Open `Run` in Windows search, type `wf.msc`, and press Enter.
2. Click **Windows Firewall Properties** (top of the left panel).
3. For **Domain, Private, and Public Profiles**, set **Firewall State** to **Off**.
4. Click **Apply** and **OK**.

<p>
<img src="https://imgur.com/Nl9jiWR.png" height="80%" width="80%" alt="Firewall">
</p>

<br>
<br>
<br>

## Step 4: 🔄 Test Connection from Client VM

1. RDP into your **Client VM**. (We are not using domain login yet)
2. Open **PowerShell** and run:  
   ```
   ping <DC_Private_IP>
   ```
3. Run:  
   ```
   ipconfig /all
   ```
4. To confirm it’s using the DC’s DNS and connected properly, look for "DNS Server", it should be linked to the DC's private IP


<p>
<img src="https://imgur.com/nx5nKxs.png" height="40%" width="70%" alt="Command Prompt">
</p>

<br>
<br>
<br>

# Step 5: 🖥️ Join Client VM to Domain

1. Log into the **Client VM** as the local Administrator.
2. Open **System Properties** (type 'Run' then `sysdm.cpl`).
3. Click **Change**, select **Domain**, and enter the domain name you set earlier (e.g., `mydomain.com`).
4. When prompted, enter **Domain Admin credentials** (the ones set during DC configuration).
5. After confirmation, **restart the Client VM**.
6. On reboot, login using: `mydomain.com\YourUser`.

<p>
<img src="https://imgur.com/EKHU4I2.png" height="80%" width="80%" alt="Joining Domain via Client VM">
</p>

<br>
<br>
<br>

# Step 6: 🧑‍💻 Allow Domain Users to Use RDP

1. Reconnect to the **Client VM** using the **DC admin account**.
2. Open **System Properties** (type 'Run' then `sysdm.cpl`)
3. Under **Remote**, click **Select Users** then **Add**
4. Type **domain users** 
5. Apply and save changes.
<p>
<img src="https://imgur.com/NMBAGxU.png" height="80%" width="80%" alt="Adjusting GP">
</p>
