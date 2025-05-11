<h1>  🛠️ Active Directory: OU, Group, and GPO Management </h1>

## ✅ Project Task Summary

- Create Organizational Units (OUs) & Security Groups
- Configure Active Directory Group Policies & Security Configuration:

## 📌 Prerequisites
- 🖥️ **Windows Server VM** promoted as a Domain Controller (DC)
- 🌐 A **Client VM** joined to the same domain
- 💼 **Active Directory Domain Services (AD DS)** installed and configured
- 📡**Remote Desktop Protocol (RDP)**
- ✅ Completed The Active Directory User Management (Previous Project)
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

- ### In Progress...

<h1> ⚙️ Project Steps ⚙️ </h1>

# 🏗️ Creating Organizational Units (OUs) & Security Groups

 ### These steps will help structure your Active Directory environment and assign permissions more efficiently. *(Required)*

---

### Step 1️⃣: Create Organizational Units (OUs)

> 📌 *Why?* OUs let you logically organize users, computers, and groups, making management and GPO application easier.

1. Open **Active Directory Users and Computers (ADUC)** on the Domain Controller.
2. In the left pane, **right-click your domain** (e.g., mydomain.com) → Hover over **New** → Click **Organizational Unit**.
3. Name the OU appropriately & create it. (create these OU examples: _ADMINS, _USERS, _COMPUTERS).
4. Within the **_USERS**, create more OUs named: IT, HR, Finance, Sales 


<br>

### Step 2️⃣: Create Security Groups

> 📌 *Why?* Security groups are used to assign permissions and apply Group Policies to sets of users.

1. In **ADUC**, navigate to the OU where you want to create the group (e.g., **IT**).
2. Right-click inside the OU → Click **New** → Select **Group** & name the group (for example, **IT-Admins**).
3. Set **Group scope** to **Global** and **Group type** to **Security**.
4. Click **OK** to create the group.
5. Create groups for each respectiv OU.
   (*create more groups for each department*)


<br>

### Step 3️⃣: Add Members to the Groups

> 📌 *Why?* Group membership allows users to inherit permissions and settings from the group policies.

1. Go to the **Default Users** & create random users for each department.
2. Double-click the newly created group (e.g., **IT-Admins**) → Go to the **Members** tab.
3. Click **Add**, type the usernames of users to include, then click **Check Names** and **OK**.


<br>

### *Example:*

<p>
<img src="https://imgur.com/qxMVqs3.png" height="65%" width="65%" alt="OU/SG Creation">
</p>


<br>
<br>
<br>

# 🛡️ Active Directory Group Policy & Security Configuration

> 📌 *Why?* Helps prevent unauthorized access by enforcing strong password practices for anyone under the domain.

## Step 1️⃣: Editing the Default Domain Policy & Enforcing Strong Password Policies

Open **Group Policy Management** on the Domain Controller.
1. Expand your domain in GPMC, Locate **Default Domain Policy** → Right-click → **Edit**.
2. Navigate to:
  Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy
3. Configure the following under Password Policy:
  - **Enforce password history**: 24 passwords remembered
  - **Maximum password age**: 90 days
  - **Minimum password length**: 12 characters
  - **Password must meet complexity requirements**: Enabled
   

<p>
<img src="https://imgur.com/wdK5Qko.png" height="85%" width="90%" alt="Password GP">
</p>

<br>

## Step 2️⃣: Enforcing Group Policy Settings for Specific Departments

>📌 *Why?* Secures administrative tasks by assigning them only to approved users.

1. In GPMC, go to the **IT-Admins** group, Right-click → **Create a GPO in this domain, and link it here** → Name: IT-Admin Policies.
2. Right-click → Edit GPO:
  - Computer Configuration → Policies → Windows Settings → Security Settings → Local Policies → User Rights Assignment
3. Grant these permissions to **IT-Admins, Administrators** group:
  - Allow Log on locally
  - Allow log on through Remote Desktop Services


<p>
<img src="https://imgur.com/xHl7F4A.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>


<br>

## Step 2️⃣.1️⃣: Restrict Access for Finance group:

> 📌 *Why?* Maintains security and compliance for sensitive departments.

1. Link a new GPO to the **Finance** OU. Name it **Finance-Restricted Policy**.
2. Right-click → Edit GPO
3. Prevent CMD access:
    User Configuration → Policies → Administrative Templates → System → Prevent access to the command prompt → Enabled
        ✅ Apply the Policy 

4. Restrict access to the C: drive:
    User Configuration → Administrative Templates → Windows Components → File Explorer → Hide specified drives in My Computer → Restrict C:
        ✅ Apply the Policy



<br>
     
<p>
<img src="https://imgur.com/s0QhENY.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>

<p>
<img src="https://imgur.com/7wRJ9c6.png" height="85%" width="90%" alt="IT-ADMIN GP">
</p>


