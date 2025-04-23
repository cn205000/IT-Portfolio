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


## Step 4️⃣: Installing OSTicket

1. On the windows VM open this link on Edge, download & extract this file onto your desktop: [OSTicket Installation Files](https://drive.google.com/file/d/118z3d-o9Oyom8FgGzbJe2iBiIVB3s1Th/view?usp=sharing)
2. Open the search bar, type & open "Turn Windows Features On or Off". Check off & expand "Internet Information Services" then follow this: World Wide Web Services -> Application Development Features -> [X] CGI then hit OK.
3. Go back to the **OSTicket Installation Files**, Open, run & click through **PHPManagerForIIS** & **rewrite_amd64** executable. 
4. 




<p>
<img src="https://imgur.com/XOezo7q.png" height="90%" width="90%" alt="RDP">
</p>
