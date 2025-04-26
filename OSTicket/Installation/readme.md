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

<p>
<img src="https://imgur.com/DXPxCjA.png" height="35%" width="35%" alt="RG Creation">
</p>

<br>

## Step 2️⃣: Create a Windows 10 Virtual Machine (VM)  
1. Go to **Virtual Machines** in Azure and click **Create** → **Azure Virtual Machine**.  
2. Under the **Basics** tab:  
   - Select the **previously created Resource Group**.
   - Pick the same **Region** for the **previously created Resource Group**.
   - Choose **Windows 10 Pro** for the image.  
3. Complete the configuration and click **Review + Create** → **Create**.

<p>
<img src="https://imgur.com/HFnUwht.png" height="40%" width="40%" alt="Windows Creation">
</p>


## Step 3️⃣: Using Remote Desktop Protocol (RDP)

1. In Azure, open your **Windows VM** and copy its **Public IP Address**.
2. On your local machine, search for and open **Remote Desktop Connection**.
3. Paste the copied IP into the **Computer** field.
4. Enter the **Windows VM username**, click **Connect**, and log in.
   
<p>
<img src="https://imgur.com/JclDJbE.png" height="90%" width="90%" alt="RDP">
</p>


## Step 4️⃣: Installing OSTicket Prerequisites 

1. On the windows VM open this link on Edge, download & extract this file onto your desktop: [OSTicket Installation Files](https://drive.google.com/file/d/118z3d-o9Oyom8FgGzbJe2iBiIVB3s1Th/view?usp=sharing)
2. Open the search bar, open up "Turn Windows Features On or Off". Check off & expand "Internet Information Services" then follow this: World Wide Web Services -> Application Development Features -> [X] CGI then hit OK.
3. Go back to the **OSTicket Installation Files**, Open, run & click through **PHPManagerForIIS** & **rewrite_amd64** executable. 
4. Open File explorer, click on **This PC** then **Windows (C:)** & create a new folder named **PHP**.
5. Go back to the **OSTicket Installation Files** & right-click extract the **php-7.3.8-nts-Win32** zipped folder into the new **PHP** Folder.
6. Open the **OSTicket Installation Files** & install the **VC_redist.x86** executable.
7. From the **osTicket-Installation-Files** folder, install **MySQL 5.5.62**
Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Username: root Password: root *(login info is for simplicity of project)*
8. Type & open on the windows search, **IIS** *(Internet Information Services)* as admin. Open **PHP Manager** & click **Register new PHP version**, browse the file explorer for the **C:\PHP** Directory then register **php-cgi**
9. Within **IIS** under **Connections** on the left, right-click on your VMs name then stop & start to restart the web server.

 

<p>
<img src="https://imgur.com/XOezo7q.png" height="90%" width="90%" alt="RDP">
</p>




## Step 5️⃣: OSTicket Installation
1. Open **OSTicket-Installation-Files**, right-click & extract the OSTicket zipped folder into the same folder.
2. In another File Explorer application, navigate to **This PC** -> **inetpub** -> **wwwroot**
3. Back In the **OSTicket-Installation-Files**, open the unzipped **OSTicket** Folder, copy the **Upload** Folder, paste it into the **wwwroot** folder & rename it to "osTicket"
4. In **IIS**, stop & start the web server again the expand **Sites** -> **Default Web Site** -> **osTicket**. Click on **osTicket** & under **Manage Folder** on the right side, open **Browse:80**
5. Go back to IIS, sites -> Default -> osTicket. Double-click PHP Manager & Click “Enable or disable an extension”. Right click and enable these extensions: 
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
6. From: **C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php** in file explorer, rename **ost-sampleconfig.php** -> **ost-config.php**.
7. Right-click **ost-config.php** -> **Properties** -> **Security** -> **Advanced** -> **Disable Inheritance** -> **Remove all permissions** -> **add** -> **Select a Principle** -> Type **Everyone** -> **OK & Full Control** -> **Apply**
8. Open the **OSTicket Web Server** & Continue. Fill out the **System Settings & Admin User** prompts. (*Note your admins username & password*)
9. Open **OSTicket-Installation-Files** & install **HeidiSQL Setup**. Click through the default prompts & Finish.
10. In **HeidiSQL** click **New**. For user & password, enter our **SQL username & password** from earlier then **open**. (*Username: root Password: root*)
11. 
