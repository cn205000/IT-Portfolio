<h1> 🌐 osTicket Post-Installation Configuring </h1>

## ✅ Project Task Summary

- Configure agent roles and access permissions
- Create departments and assign responsibilities
- Add test agents and users
- Form agent teams based on support needs
- Set up SLA (Service Level Agreements) for ticket prioritization

## 📌 Prerequisites

- 🌐 Internet connection
- ✅ Completed osTicket installation and basic setup (Previous Project)
- 💻 Windows 10 VM with a functional osTicket instance
- 🧠 Basic Intuition of ticketing workflows and support roles

## 🔗 Environments & Technologies Used 

- **Windows 10 VM**
- **osTicket**
- **Web Browser**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)


<h1> ⚙️ osTicket Configuring ⚙️ </h1>


## 1️⃣: Roles

*Roles define what permissions a group of agents has. You can create or edit roles to allow or restrict access across different areas of the helpdesk.*

1. Log in to the [Admin Control Panel](http://localhost/osTicket/scp/login.php) and click **Admin Panel** in the top-right corner.
2. Go to **Admin Panel → Agents → Roles**.
3. Click **Add New Role**, name it **Supreme Admin**, then click the **Permissions** tab.
4. Under **Tickets**, **Tasks**, and **Knowledgebase**, check all boxes to give full access.  
   *(A Supreme Admin should have control over everything.)*

<p>
<img src="https://imgur.com/li5othi.png" height="80%" width="80%" alt="Roles Example">
</p>

---

## 2️⃣: Departments

*Departments organize and route tickets to the appropriate group or team, such as a “Support” or “SysAdmin” department.*

1. Go to **Admin Panel → Agents → Departments**.
2. Click **Add New Department** and fill in the following:
   - **Parent:** Top-Level Department  
   - **Name:** SysAdmins  
   *(Other options can be adjusted as needed.)*

<p>
<img src="https://imgur.com/h3EWsqe.png" height="80%" width="80%" alt="Department Example">
</p>

---

## 3️⃣: Agents

*Agents are your internal support staff. They handle tickets and can be assigned to departments, roles, and teams. 
Note down the agents login info for future use.*

1. Go to **Admin Panel → Agents → Add New Agent**.
2. Create two test agents with made-up names and emails.
3. Set their passwords manually:
   - Click **Set Password**
   - Uncheck **Send password reset email** and **Require password change**
4. Assign the following:

- **Agent One**
  - Department Access: **Support / SysAdmins** with **All Access**
  - Team: **Online Banking**

- **Agent Two**
  - Department Access: **Support** with **Expanded Access**
  - Team: **Level I Support**

<p>
<img src="https://imgur.com/Y3ll9Jg.png" height="60%" width="60%" alt="Agent Example">
</p>

---

## 4️⃣: Users

*Users are the people who submit support tickets — typically customers or clients. Note down the User login info for future use.*

1. Go to **Agent Panel → Users → Add New**.
2. Fill in fake user details to simulate a real support ticket.

<p>
<img src="https://imgur.com/LqV8kMp.png" height="90%" width="90%" alt="User Example">
</p>

---

## 5️⃣: Teams

*Teams are custom groups of agents from different departments, built to handle specialized ticket types (e.g., Online Banking issues).*

1. Go to **Admin Panel → Agents → Teams**.
2. Click **Add New Team** and name it **Online Banking**. Do the same with **Level I Support**.
3. After creating the team, use the **Members** tab to add agents to it.
   Add:
   - SysAdmins + Admin to **Online Banking**
   - Support to **Level I Support**

<p>
<img src="https://imgur.com/tC6Qjhw.png" height="90%" width="90%" alt="Team Example">
</p>

---

## 6️⃣: SLA (Service Level Agreements)

*SLAs define how quickly tickets should be responded to or resolved based on priority.*

1. Go to **Admin Panel → Manage → SLA**.
2. Create the following SLAs:
   - **Sev-A**: 1-hour grace period, 24/7 schedule  
   - **Sev-B**: 4-hour grace period, 24/7 schedule  
   - **Sev-C**: 8-hour grace period, business hours only

<p>
<img src="https://imgur.com/geXtlEu.png" height="90%" width="90%" alt="SLA Example">
</p>


