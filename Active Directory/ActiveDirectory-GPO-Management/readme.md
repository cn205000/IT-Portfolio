<h1>  🛠️ Active Directory: OU, Group, and GPO Management </h1>

## ✅ Project Task Summary

- [ ] Creating Organizational Units (OUs) & Security Groups
- [ ] Configuring Active Directory Group Policies & Security Configuration:
- [ ] Network Drive Mapping via Logon Script

## 📌 Prerequisites
- 🖥️ **Windows Server VM** promoted as a Domain Controller (DC)
- 🌐 A **Client VM** joined to the same domain
- 💼 **Active Directory Domain Services (AD DS)** installed and configured
- 📡**Remote Desktop Protocol (RDP)**
- 🧠 **Basic understanding of:**
  - Organizational Units (OUs)
  - Group Policies
    
## 🔗 Enviroments & Technologies Used 
-  Microsoft Azure
-  2022 Windows Server
-  Windows 10 Pro
-  Remote Desktop Protocol
-  Active Directory Users and Computers (ADUC)
-  Group Policy Management (GPMC)

  ## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps </h1>

# 🏗️ Creating Organizational Units (OUs) & Security Groups

 ### These steps will help structure your Active Directory environment and assign permissions more efficiently. *(Required)*

---

### Step 1️⃣: Create Organizational Units (OUs)

1. Open **Active Directory Users and Computers (ADUC)** on the Domain Controller.
2. In the left pane, **right-click your domain** (e.g., mydomain.com) → Hover over **New** → Click **Organizational Unit**.
3. Name the OU appropriately & create it. (create these OU examples: _ADMINS, _USERS, _COMPUTERS).
4. Within the **_USERS**, create more OUs named: IT, HR, Finance, Sales 

> 📌 *Why?* OUs let you logically organize users, computers, and groups, making management and GPO application easier.

<br>

### Step 2️⃣: Create Security Groups

1. In **ADUC**, navigate to the OU where you want to create the group (e.g., **IT**).
2. Right-click inside the OU → Click **New** → Select **Group**.
3. Name the group (for example, **IT-Admins**).
4. Set **Group scope** to **Global** and **Group type** to **Security**.
5. Click **OK** to create the group.
   (*create more groups for each department*)

> 📌 *Why?* Security groups are used to assign permissions and apply Group Policies to sets of users.

<br>

### Step 3️⃣: Add Members to the Groups

1. Double-click the newly created group (e.g., **IT-Admins**) → Go to the **Members** tab.
2. Click **Add**, type the usernames of users to include, then click **Check Names** and **OK**.

> 📌 *Why?* Group membership allows users to inherit permissions and settings from the group policies.

<br>

### *Example:*

<p>
<img src="https://imgur.com/qxMVqs3.png" height="65%" width="65%" alt="OU/SG Creation">
</p>


<br>
<br>
<br>

# 🛡️ Active Directory Group Policy & Security Configuration

## Step 1️⃣: Editing the Default Domain Policy & Enforcing Strong Password Policies
Open **Group Policy Management** on the Domain Controller.
1. Expand your domain in GPMC.
2. Locate **Default Domain Policy** → Right-click → **Edit**.
3. Navigate to:
  Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy
🔹 Configure the following under Password Policy:
4. **Enforce password history**: 24 passwords remembered
5. **Maximum password age**: 90 days
6. **Minimum password length**: 12 characters
7. **Password must meet complexity requirements**: Enabled
   
📌 **Why?** Helps prevent unauthorized access by enforcing strong password practices for anyone under the domain.

<p>
<img src="https://imgur.com/wdK5Qko.png" height="85%" width="90%" alt="Password GP">
</p>

<br>

## Step 2️⃣: Enforcing Group Policy Settings for Specific Departments
1. In GPMC, go to the **IT-Admins** group.
2. Right-click → **Create a GPO in this domain, and link it here** → Name: IT-Admin Policies.
3. Right-click → Edit GPO:
  - Computer Configuration → Windows Settings → Security Settings → Local Policies → User Rights Assignment
4. Grant these permissions to **IT-Admins, Administrators** group:
  - Log on locally
  - Allow log on through Remote Desktop Services

📌 **Why?** Secures administrative tasks by assigning them only to approved users.

<p>
<img src="https://imgur.com/xHl7F4A.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>


<br>

## Step 2️⃣.1️⃣: Restrict Access for Finance group:
1. Link a new GPO to the **Finance** OU. Name it **Finance-Restricted Policy**.
2. Right-click Edit GPO
3. Prevent CMD access:
    User Configuration → Policies → Administrative Templates → System → Prevent access to the command prompt → Enabled
        ✅ Apply the Policy 

4. Restrict access to the C: drive:
    User Configuration → Windows Components → File Explorer → Hide specified drives in My Computer → Restrict C:
        ✅ Apply the Policy

📌 **Why?** Maintains security and compliance for sensitive departments.

<br>
     
<p>
<img src="https://imgur.com/s0QhENY.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>

<p>
<img src="https://imgur.com/7wRJ9c6.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>

<br>

## Step 3️⃣: Confirm Changes
1. Log in as Finance user on Client VM
2. CMD should be blocked.
3. The C: drive access is hidden.

<br>
<br>
<br>

# 🚀 Network Drive Mapping via Logon Script
📌 **Why?** Automatically maps shared drives for users at login, ensuring consistent and easy access to network resources.

### Step 1️⃣: Create Shared Network Folder
1. On Domain Controller go to **C:** on File Explorer → Create new folder & rename.
2. Right-click folder → **Properties** → **Sharing** tab → **Advanced Sharing...**.
3. Check ✅ **"Share this folder"**.
4. **Permissions**:
  - **Authenticated Users**: Full Control (if needed)
  - **Administrators**: Full Control
 The folder can now be accessed this way: (\\DOMAIN HERE\FOLDER NAME HERE)

<br>

### Step 2️⃣: Create Logon Script
1. Open **Notepad**, paste:
  net use G: \\DOMAIN HERE\FOLDER NAME HERE /persistent:yes
2. Save this as map-drive.bat & save it in this path: (\\DOMAIN HERE\NETLOGON)

<br>

### Step 3️⃣: Assign Script via Group Policy
1. Open GPMC → Expand domain → Right-click an OU (has a group and user assigned to it) → Edit.
2. Navigate to:
  User Configuration → Policies → Windows Settings → Scripts (Logon/Logoff) → Logon
3. Double-click **Logon** → Click **Add** → Browse and type in the **NETLOGON** path from earlier.
4. Select map-drive.bat & apply 

<br>

### Step 4️⃣: Apply and Test
1. On a domain-joined PC, open cmd and type:
   gpupdate /force
2. Log out/in as a domain user.
3. Open **File Explorer** → G: drive should appear.

