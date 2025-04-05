# 🛠️ Configuring Users Within Active Directory

## ✅ Project Task Summary

- [ ] Creating Users
- [ ] Configuring User Privileges
- [ ] Managing User Accounts

## 📌 Prerequisites
- 🖥️ **Windows Server VM** promoted as a Domain Controller (DC)
- 🌐 A **Client VM** joined to the same domain
- 💼 **Active Directory Domain Services (AD DS)** installed and configured
- 📡**Remote Desktop Protocol (RDP)**
- 🧠 Basic understanding of:
  - Organizational Units (OUs)
  - Group Policy
  - Domain vs. Local accounts

    
## 🔗 Enviroments & Technologies Used 
-  Microsoft Azure
-  2022 Windows Server
-  Windows 10 Pro
-  Remote Desktop Protocol
-  Active Directory Users and Computers (ADUC)

  ## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

# *Installation Steps*

## 🏗️ Creating Organizational Units (OUs) & Security Groups

 ### These steps will help structure your Active Directory environment and assign permissions more efficiently. *(Required)*

---

### 1️⃣ Create Organizational Units (OUs)

1. Open **Active Directory Users and Computers (ADUC)** on the Domain Controller.
2. In the left pane, **right-click your domain** (e.g., mydomain.com) → Hover over **New** → Click **Organizational Unit**.
3. Name the OU appropriately & create. (create these OU examples: _ADMINS, _USERS, _COMPUTERS).
4. Within the **_USERS**, create more OU's named: IT, HR, Finance, Sales 

> 📌 *Why?* OUs let you logically organize users, computers, and groups, making management and GPO application easier.


### 2️⃣ Create Security Groups

1. In **ADUC**, navigate to the OU where you want to create the group (e.g., **IT**).
2. Right-click inside the OU → Click **New** → Select **Group**.
3. Name the group (example: **IT-Admins**).
4. Set **Group scope** to **Global** and **Group type** to **Security**.
5. Click **OK** to create the group.
   (*create more groups for each department*)

> 📌 *Why?* Security groups are used to assign permissions and apply Group Policies to sets of users.


### 3️⃣ Add Members to the Groups

1. Double-click the newly created group (e.g., **IT-Admins**) → Go to the **Members** tab.
2. Click **Add**, type the usernames of users to include, then click **Check Names** and **OK**.

> 📌 *Why?* Group membership allows users to inherit permissions and settings from the group policies.

### *Example*

<IMAGE>




# 🛡️ Active Directory Group Policy & Security Configuration

## 1️⃣ Editing the Default Domain Policy
Open **Group Policy Management** on the Domain Controller.
1. Expand your domain in GPMC.
2. Locate **Default Domain Policy** → Right-click → **Edit**.
3. Navigate to:
  Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy

  ## 1️⃣.2️⃣ Enforcing Strong Password Policies
🔹 Configure the following under Password Policy:
1. **Enforce password history**: 24 passwords remembered
2. **Maximum password age**: 90 days
3. **Minimum password length**: 12 characters
4. **Password must meet complexity requirements**: Enabled

📌 **Why?** Helps prevent unauthorized access by enforcing strong password practices for anyone under the domain.


## 2️⃣ Enforcing Group Policy Settings for Specific Departments
1. In GPMC go to **IT-Admins** group.
2. Right-click → **Create a GPO in this domain, and link it here** → Name: IT-Admin Policies.
3. Right Click → Edit GPO:
  - Computer Configuration → Windows Settings → Security Settings → Local Policies → User Rights Assignment
4. Grant these permissions to **IT-Admins** group:
  - Log on locally
  - Allow log on through Remote Desktop Services

📌 **Why?** Secures administrative tasks by assigning them only to approved users.


## 2️⃣.1️⃣ Restrict Access for Finance group:
1. Create a new GPO and link it to the **Finance** OU. Name it **Finance-Restricted Policy**.
2. Right-click Edit GPO
  
  3. Prevent CMD access:
    User Configuration → Administrative Templates → System → Prevent access to the command prompt → Enabled
        ✅ Apply the Policy
    
  4. Restrict access to C: drive:
    User Configuration → Windows Components → File Explorer → Hide specified drives in My Computer → Restrict C:
        ✅ Apply the Policy

## 3️⃣ Confirm Changes
1. Log in as Finance user on Client VM
2. CMD should be blocked.
3. C:\ drive access hidden.

📌 **Why?** Maintains security and compliance for sensitive departments.


## 🚀 Network Drive Mapping via Logon Script

### Step 1: Create Shared Network Folder
1. On Domain Controller:
  - Go to **C:** on File Explorer → Create new folder & rename.
  - Right-click folder → **Properties** → **Sharing** tab → **Advanced Sharing...**.
  - Check ✅ **"Share this folder"**.
  - **Permissions**:
    - **Authenticated Users**: Full Control (if needed)
    - **Administrators**: Full Control
 The folder can now be accesed this way: (\\DOMAIN HERE\FOLDER NAME HERE)


### Step 2: Create Logon Script
- Open **Notepad**, paste:
  net use G: \\DOMAIN HERE\FOLDER NAME HERE /persistent:yes
- Save this as map-drive.bat & save it in this path: (\\DOMAIN HERE\NETLOGON)


### Step 3: Assign Script via Group Policy
- Open GPMC → Expand domain → Right-click an OU (has a group and user assigned to it) → Edit.
- Navigate to:
  User Configuration → Policies → Windows Settings → Scripts (Logon/Logoff) → Logon
- Double-click **Logon** → Click **Add** → Browse and type in the **NETLOGON** path from earlier.
- select map-drive.bat & apply 


### Step 4: Apply and Test
1. On a domain-joined PC, open cmd and type:
   gpupdate /force
2. Log out/in as a domain user.
3. Open **File Explorer** → G: drive should appear.

📌 **Why?** Ensures centralized and consistent access to shared resources.
