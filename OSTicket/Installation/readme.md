<h1> 🌐 osTicket Installation with Prerequisites </h1>

## ✅ Project Task Summary

- Create a Windows 10 VM in Azure and connect via RDP  
- Configure all required osTicket prerequisites (IIS, PHP, MySQL, PHP extensions)  
- Install and configure osTicket web application  

## 📌 Prerequisites

- 🔐 Microsoft Azure Account 
- 🌐 Internet connection  
- 💻 Remote Desktop Client (RDP)  
- 🧠 Basic understanding of Windows OS, and file system navigation  

## 🔗 Environments & Technologies Used

- **Microsoft Azure**  
- **Windows 10 Virtual Machine**  
- **IIS (Internet Information Services)**  
- **PHP NTS for Windows**  
- **MySQL**  
- **HeidiSQL**  
- **osTicket**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>


## Step 1️⃣: Create a Resource Group  

>📌 *Why?* A resource group keeps all related resources (VMs, storage, network) organized under one container in Azure.


1. In the Azure Portal, navigate to **Resource Groups**.  
2. Click **Create**, enter a name, choose a region, then click **Review + Create** → **Create**.

<p>
<img src="https://imgur.com/DXPxCjA.png" height="35%" width="35%" alt="RG Creation">
</p>

<br>

## Step 2️⃣: Create a Windows 10 Virtual Machine (VM)  

>📌 *Why?* The Windows 10 VM will host the web server environment where osTicket will be installed.

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

>📌 *Why?* RDP lets you connect to and control the VM directly to install and configure software.

1. In Azure, open your **Windows VM** and copy its **Public IP Address**.
2. On your local machine, search for and open **Remote Desktop Connection**.
3. Paste the copied IP into the **Computer** field.
4. Enter the **Windows VM username**, click **Connect**, and log in.
   
<p>
<img src="https://imgur.com/JclDJbE.png" height="90%" width="90%" alt="RDP">
</p>


## Step 4️⃣: Installing OSTicket Prerequisites 

>📌 *Why?* These prerequisites (IIS, PHP, MySQL) are required to run osTicket as a functional web-based ticketing system.

1. On the **Windows VM**, open **Edge**, download & extract the [OSTicket Installation Files](https://drive.google.com/file/d/118z3d-o9Oyom8FgGzbJe2iBiIVB3s1Th/view?usp=sharing) onto your desktop.
2. Windows search for **"Turn Windows Features On or Off"**. Open it & expand **Internet Information Services (IIS)** → World Wide Web Services → Application Development Features → check **CGI**, then click **OK**.
3. In the **OSTicket Installation Files**, run and install **PHPManagerForIIS** and **rewrite_amd64**.
4. In **File Explorer**, go to **This PC → C:** and create a new folder named **PHP**.
5. Extract **php-7.3.8-nts-Win32** into the newly created **PHP** folder.
6. Install **VC_redist.x86** from the **OSTicket Installation Files**.
7. Install **MySQL 5.5.62**:
   - Choose **Typical Setup** → Launch Configuration Wizard → Standard Configuration.
   - Set **Username: root** **Password: root** (for simplicity in this project).
8. Open **IIS Manager** as Administrator → In **PHP Manager**, click **Register new PHP version** → Browse to **C:\PHP\php-cgi.exe** and register it.
9. In **IIS**, right-click the VM's name under **Connections** → **Start & Stop** to apply all changes.
 

<p>
<img src="https://imgur.com/XOezo7q.png" height="90%" width="90%" alt="RDP">
</p>




## Step 5️⃣: OSTicket Installation

>📌 *Why?* This step installs and launches osTicket, setting up the core helpdesk application for use and management.

1. In the **OSTicket Installation Files**, extract the **OSTicket** zipped folder.
2. Open **File Explorer** → **This PC → (C:) → inetpub → wwwroot**.
3. Copy the **Upload** folder in the exetracted **OSTicket** zipped folder → Paste it into **wwwroot** → Rename it to **osTicket**.
4. In **IIS**, restart the server → Expand **Sites → Default Web Site → osTicket** → Click **osTicket** → On the right panel, click **Browse:80** to open it in the browser.
5. Enable required PHP Extensions in IIS:
   - Double-click **PHP Manager** → **Enable or Disable an Extension** → Right-click and enable:
     - **php_imap.dll**
     - **php_intl.dll**
     - **php_opcache.dll**
6. Rename the file at **C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php** → **ost-config.php**.
7. Modify **ost-config.php** permissions:
   - Right-click → **Properties → Security → Advanced → Disable Inheritance → Remove all permissions → Add** → Select **Everyone → Grant Full Control → Apply**.
8. Refresh the **osTicket Web Installer** page → Fill in **System Settings** and **Admin User** information (note the credentials).
9. Install **HeidiSQL** from the **OSTicket Installation Files** (default setup).
10. In **HeidiSQL**:
    - Click **New** → Enter **Username: root** and **Password: root** → Click **Open**.
11. Right-click the unnamed connection → **Create New → Database** → Name it **osTicket**.
12. On the **osTicket Web Installer**, input:
    - **MySQL Database:** osTicket
    - **MySQL Username:** root
    - **MySQL Password:** root
13. Click **Install!** 🎉

<p>
<img src="https://imgur.com/XOezo7q.png" height="90%" width="90%" alt="RDP">
</p>
