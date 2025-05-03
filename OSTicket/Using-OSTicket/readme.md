<h1> 🌐 osTicket Post-Installation Configuring </h1>

## ✅ Project Task Summary

- Staff Configuration
- SLA Configuration


## 📌 Prerequisites
- 🌐 Internet connection
- ✅ Have gone through & finished the previous project in the repository.
  
## 🔗 Enviroments & Technologies Used 
-  **Windows 10 VM**
-  **osTicket**
## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Ticket Cycle ⚙️ </h1>


## 1️⃣: Creating Ticket as End-User
*For this scenario, we'll imagine a banking system has gone down within the company and our user is creating the ticket for this problem*

1. Open the [End-Users osTicket](http://localhost/osTicket), click **Open A New Ticket** in the top-right corner.
2. Log in with the **User** info we made in the previous portfolio.
3. Enter similar details below (*Write ticket as if you're in the end-user's situation.*)
  - **Help Topic** = Report A Problem / Access Issue
  - **Issue Summary** = online banking system is down/non-accessible
  - **Details** =  *My employees are reporting that the online banking portal is not accessible, and the ones who can get to the portal are unable to log in.*
4. Create ticket.

<p>
<img src="" height="80%" width="80%" alt="Roles Example">
</p>

---

## 2️⃣: Assign the Ticket as Support Agent

1. Log in to the [Admin Control Panel](http://localhost/osTicket/scp/login.php) as an agent from previous project & open the ticket.
2. We'll select SLA as **Sev-A** & comment. (*Sev-A because the issue has a big impact and needs to be resolved ASAP.*)
3. Assign the ticket to the **Online Banking Team** & comment.
4. Set priority status to **High**.


<p>
<img src="" height="80%" width="80%" alt="Department Example">
</p>

---

## 3️⃣: Pickup ticket as support
*Lets act like we're working the ticket & we resolved the problem as the Online Banking Support agent.*

1. Log out of the **Level I Support agent** & login as the **Online Banking Support agent**.
  *Imagine we recently rolled out a new update, we could assume this is a leading cause to the issue.* 
3. Open the ticket & comment on what we're going to do & what we suspect the problem is.
   (*ex: I suspect the issue could be related to the new updates that were released. I will reroll the update if needed after looking into it further and observe if anything has changed.*)
4. Comment that the reroll has fixed the issue & set ticket status to Resolved.



<p>
<img src="" height="90%" width="90%" alt="Team Example">
</p>



