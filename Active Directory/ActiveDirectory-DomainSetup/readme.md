# 🛠️ Configuring a Domain Controller & Active Directory

### This project walks you through setting up your Domain Controller
---
## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)


## 📌 Prerequisites
- **Azure subscription** (Free or Paid)
  
## 🔗 Enviroments & Technologies Used 
-  **Azure**

# *Installation Steps*

## Step 1: 🔐 Using Remote Desktop Protocol (RDP)

1. Go to your **Domain Controller VM** on Azure and copy the **Public IP Address**.
2. On your Windows search bar, search for **Remote Desktop Connection** and open it.
3. Paste the IP into the box labeled **Computer**.
4. Enter the **username and password** you configured for the Domain Controller VM.
5. Click **Connect** and login.

<p>
<img src="https://imgur.com/ALp3vCX.png" height="65%" width="65%" alt="RG Creation">
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
<img src="https://imgur.com/rjS0CS4.png" height="50%" width="50%" alt="VNET Creation">
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
<img src="https://imgur.com/K5tdnW3.png" height="20%" width="50%" alt="DC Creation">
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
4. To confirm it’s using the DC’s DNS and connected properly, look for


<p>
<img src="https://imgur.com/CO3c8ik.png" height="20%" width="50%" alt="Client-VM Creation">
</p>

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
