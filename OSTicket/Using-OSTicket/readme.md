<h1> 🌐 osTicket Ticket Cycle </h1>

## ✅ Project Task Summary

- Simulate a real-world IT support ticket from start to resolution
- Submit a ticket as an end-user
- Assign, prioritize, and apply SLA to the ticket as a support agent
- Troubleshoot and resolve the issue as a specialist agent

## 📌 Prerequisites

- 🌐 Internet connection
- 💻 osTicket fully installed and configured
- ✅ Completion of the previous osTicket configuration project (Roles, Departments, Teams, Agents, Users, SLA setup)
- 🧠 Basic understanding of IT ticketing systems and service-level workflows

## 🔗 Environments & Technologies Used 

- **Windows 10 VM**
- **osTicket**
- **Web Browser**
- **Localhost (Apache/IIS) Web Server Environment**

## 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h1> ⚙️ Ticket Cycle ⚙️ </h1>


## 1️⃣: Creating a Ticket as an End-User
> 📌 *Why?* Creating a ticket simulates how real users report issues. It helps kick off the support process and gives agents the necessary information to respond.

 > *In this scenario, imagine a user is reporting that the company’s online banking system is down.*

1. Go to the [End-User osTicket Portal](http://localhost/osTicket) and click **Open A New Ticket**.
2. Log in using the test user account created earlier.
3. Fill out the ticket details as if you're the user:
   - **Help Topic**: Report a Problem / Access Issue  
   - **Issue Summary**: Online banking system is down  
   - **Details**: *Employees report that the banking portal is inaccessible. Those who can access it are unable to log in.*
4. Click **Create Ticket**.

<p>
<img src="" height="80%" width="80%" alt="Creating Ticket">
</p>

---

## 2️⃣: Assigning the Ticket as a Support Agent

> 📌 *Why?* Assigning the ticket and setting SLA ensures the right team sees it fast and knows how critical the issue is, helping with quicker response times.

1. Log in to the [Admin Control Panel](http://localhost/osTicket/scp/login.php) as the support agent.
2. Open the ticket and:
   - Set the **SLA Plan** to **Sev-A** (*High urgency—system-wide outage*).
   - Add a comment explaining the urgency.
3. Assign the ticket to the **Online Banking Team**.
4. Set **Priority** to **High** and add another comment if needed.

<p>
<img src="" height="80%" width="80%" alt="Assign Ticket">
</p>

---

## 3️⃣: Resolving the Ticket as Online Banking Support

>📌 *Why?* Acting as the specialist agent helps simulate how real IT support investigates, documents, and resolves issues in a structured way.

> *Now act as the Online Banking agent responsible for resolving the issue.*

1. Log out of the current agent account and log in as the **Online Banking Support Agent**.
2. Open the ticket and comment your approach:
   - Example: *I suspect this issue is related to the recent update. I’ll investigate and roll back the update if needed.*
3. After testing and confirming, comment that the issue is resolved & the solution.
4. Change the ticket **Status** to **Resolved**.

<p>
<img src="" height="90%" width="90%" alt="Resolve Ticket">
</p>


