<h1> 🛠️ Configuring Users Within Active Directory </h1>

## ✅ Project Task Summary

- [ ] Create Users
- [ ] Configure User Privileges
- [ ] Manage User Accounts

## 📌 Prerequisites
- 🖥️ **Windows Server VM** promoted as a Domain Controller (DC)
- 🌐 A **Client VM** joined to the same domain
- 💼 **Active Directory Domain Services (AD DS)** installed and configured
- 📡**Remote Desktop Protocol (RDP)**
- 🧠 **Basic understanding of:**
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

<h1> Installation Steps </h1>

## Step 1️⃣: Creating an Admin User in Active Directory

1. Open **Active Directory Users and Computers (ADUC)** by running `dsa.msc`.
2. Right-click your domain in ADUC, go to New > Organizational Unit, and name it _ADMINS for Domain Admins.
3. Right-click the newly created OU and select **New > User**.
4. Enter a name for the user (e.g., `ITAdmin01`).
5. Set an initial password.
6. Uncheck **"User must change password at next logon"** (for admin accounts).
7. Click **Next**, then **Finish**.

> 📌 *Why?* This sets up an admin account with elevated privileges for managing users and AD settings.
<p>
<img src="https://imgur.com/gJK152u.png" height="75%" width="75%" alt="RDP">
</p>

<br>
<br>

## Step 2️⃣: Assigning Admin Privileges

1. Right-click the new user (e.g., `ITAdmin01`) → **Properties**.
2. Go to the **Member Of** tab → Click **Add**.
3. Type **Domain Admins**, then click **Apply** → **OK**.

> 📌 *Why?* Adding the user to the **Domain Admins** group gives them full administrative rights over Active Directory.

 
<p>
<img src="https://imgur.com/BkseNo2.png" height="85%" width="85%" alt="Server Manager">
</p>

<br>
<br>

## Step 3️⃣: Creating a Standard User (New Employee)

1. Open **ADUC** → Right-click on the **Users** container → **New > User**.
2. Enter the user's **First and Last Name**.
3. Set an initial password.
4. Uncheck **"Password never expires"**.
5. Keep **"User must change password at next logon"** unchecked! (We're only doing this for RDP Issues)
6. Click **Next**, then **Finish**.

> 📌 *Why?* Simulates onboarding a new employee with standard domain-level access.

<p>
<img src="https://imgur.com/FF97f1z.png" height="30%" width="60%" alt="Firewall">
</p>

<br>
<br>

## Step 4️⃣: Managing User Accounts (Day-to-Day IT Tasks)

1. Resetting Passwords
  - Right-click the user → **Reset Password** → Enter new password.

2. Disabling or Removing Users
  - Right-click the user → **Disable Account** (useful when offboarding).
  - To delete a user: Right-click → **Delete**.

3. Modifying User Properties
  - Open a user's **Properties** to configure:
  - **Profile Path** (for Roaming Profiles)
  - **Logon Hours** (set login time restrictions)
  - **Group Memberships** (adjust user permissions)

> 📌 *Why?* These are daily tasks for IT Help Desk & System Admins to maintain user access and security.



<p>
<img src="https://imgur.com/mUejQPQ.png" height="40%" width="70%" alt="Command Prompt">
</p>

<br>
<br>

## Step 5️⃣: Verifying User Login & Password Policy

1. On the **Client VM**, login as the **new user**.
2. On the **Admin VM**, go to the **new user account** and select **"Reset password at next login"**.
3. Back on the **Client VM**, open **Command Prompt** and run the following command to update Group Policy: *gpupdate /force*
4. Press **Ctrl + Fn + Alt + End** to lock the **Client VM**.
5. Attempt to **log in again** with the new user’s credentials.
6. The system will prompt the user to **change their password**.

📌 **Why?** This ensures users comply with password policies before accessing resources.

