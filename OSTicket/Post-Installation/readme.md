<h1> 🌐 osTicket Post-Installation Configuring </h1>

## ✅ Project Task Summary

- [ ] Staff Configuration
- [ ] SLA Configuration


## 📌 Prerequisites
- 🌐 Internet connection
- ✅ Have osTicket installed on a Windows VM
  
## 🔗 Enviroments & Technologies Used 
-  **Windows 10 VM**
-  **osTicket**
## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Project Steps ⚙️ </h1>


## Step 1️⃣: Configuring Roles
 *Roles are for group permissions. We can add or edit a role to give/deny access for certain permissions for a whole group of people.*
 <br>
1. Login to [Admin Control Panel](http://localhost/osTicket/scp/login.php ) & click on Admin Panel in top right.
2. **Admin Panel -> Agents -> Roles**
3. Click **Add New Role** & name it *Supreme Admin*, then click on **Permissions** 
4. Under *tickets*, *Tasks*, & *Knowledgebase* we can check off every box.
   <br>
   (For a *Supreme Admin*, we'd want them to be able to manage everything)


<p>
<img src="" height="35%" width="35%" alt="RG Creation">
</p>

<br>

## Step 2️⃣: Configuring Departments
*Departments are used to organize incoming tickets by a group/team. Departments represent certain groups, like a "Support Department," and help route the ticket to the correct staff.*
<br>
1. **Admin Panel -> Agents -> Departments**
2. Click **Add New Department**. Fill out & Create:
   - Parent: Support
   - Name: SysAdmins

  *Most of these settings are self-explanatory if you'd like to delve deeper.*

<p>
<img src="" height="40%" width="40%" alt="Windows Creation">
</p>


## Step 3️⃣: Configuring Teams
*Teams are for making a "Team" of agents from different groups. Certain IT-level support could be on a team for an online banking system.*
<br>
1. **Admin Panel -> Agents -> Departments**
2. Click **Add New Team**. Fill out & Create:
   - Name: Online Banking

*we can pre-add members to this team under the "Members" tab*

   
<p>
<img src="" height="90%" width="90%" alt="RDP">
</p>


## Step 4️⃣: Configuring Agents
*Let's create agents for the Online banking team we made earlier*
<br>
1. Admin Panel -> Agents -> Add New Agent
2. Fill out fake info for two imaginary agents 
3. Click **Set Password**, **Uncheck** 'Send Password reset email' & 'Require Password change' & set a password.
4. For their properties, assign these:
   <br>
- **Agent One**
   - Access: **Support / SysAdmins** with **All Access**
   - Teams: **Online Banking**
   <br>
- **Agent Two**
   - Access: **Support** with **Limited Access**
   - Teams: **Online Banking**
<p>
<img src="" height="90%" width="90%" alt="RDP">
</p>




## Step 5️⃣: Configuring Users
1. 


<p>
<img src="" height="90%" width="90%" alt="RDP">
</p>

## Step 6️⃣: Configuring SLA
1.




<p>
<img src="" height="90%" width="90%" alt="RDP">
</p>
