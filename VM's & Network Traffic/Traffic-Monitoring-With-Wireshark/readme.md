<h1> 🌐 Traffic Monitoring Between Two Azure VMs with Wireshark </h1>

## ✅ Project Task Summary
 
- Use RDP to connect to the Windows VM  
- Install and configure Wireshark for traffic monitoring  
- Capture, block, and analyze ICMP and SSH traffic between VMs  

## 📌 Prerequisites

- 🔐 Microsoft Azure Account  
- 🌐 Stable internet connection  
- ✅ Completion of the previous VM provisioning project 
- 🧠 Basic understanding of:
  - **ICMP** and **SSH** protocols  
  - **Azure**  

## 🔗 Environments & Technologies Used 

- **Microsoft Azure**  
- **Windows 10 Pro VM**  
- **Ubuntu 22.04 Linux VM**  
- **Wireshark**  
- **Remote Desktop Protocol (RDP)**  

# 🎥 Video Demonstration

- ## [Video Tutorial](https://youtu.be/Ji-L0qpi9ug)

<h1> ⚙️ Project Steps ⚙️ </h1>

## Step 1️⃣: Using Remote Desktop Protocol (RDP)

 > 📌 *Why?* Establishing a secure RDP connection allows remote access and management of the Windows VM to perform network monitoring tasks.

1. In Azure, open your **Windows VM** and copy its **Public IP Address**.
2. On your local machine, search for and open **Remote Desktop Connection**.
3. Paste the copied IP into the **Computer** field.
4. Enter the **Windows VM username**, click **Connect**, and log in.




<p>
<img src="https://imgur.com/JclDJbE.png" height="90%" width="90%" alt="RDP">
</p>


<br>
<br>

## Step 2️⃣: Installing Wireshark on Windows VM 

> 📌 *Why?* Wireshark provides the tools needed to capture and analyze network traffic for deeper inspection of communication between VMs.

1. After connecting to the **Windows VM**, open **Microsoft Edge**.
2. Go to: www.wireshark.org/#downloadLink
3. Download the **Windows x64 Installer**, launch it, and install using the default settings.




<p>
<img src="https://imgur.com/VAInGnm.png" height="90%" width="90%" alt="Wireshark Installation">
</p>


<br>
<br>

## Step 3️⃣: Capturing ICMP Traffic in Wireshark

> 📌 *Why?* Capturing ICMP traffic verifies basic network connectivity between two VMs and validates that packets are successfully transmitted.

1. On the **Windows VM**, open **Wireshark** via the Start menu.
2. Select the **Ethernet interface**, then in the filter bar type: icmp & press **Enter** to apply the filter.
3. In Azure, locate your **Linux VM** and copy its **Private IP address**.
4. Back on the **Windows VM**, open **PowerShell** and run: ping <Linux Private IP>
5. You should immediately see ICMP ping traffic appear in **Wireshark**.

<p>
<img src="https://imgur.com/A7yqmNX.png" height="70%" width="70%" alt="Pinging LinuxVM">
</p>


<br>
<br>

## Step 4️⃣: Block ICMP Traffic Using NSG Rules

> 📌 *Why?* Blocking ICMP traffic demonstrates how network security groups (NSGs) can control communication and protect cloud resources.

1.  On the **Windows VM**, run a continuous ping to the **Linux VM** using: ping <Linux Private IP> -t
2. In Azure, go to the **Linux VM** > **Networking** > **Network Settings**.
3. Under *Essentials*, click on the **Network Security Group (NSG)**.
4. Navigate to **Settings** > **Inbound Security Rules** → Click **Add**.
5. Set the following values:  
  - **Destination Port Ranges**: `*`  
  - **Protocol**: `ICMP`  
  - **Action**: `Deny`  
  - **Priority**: `290`  
  → Then click **Add**.
6. Return to the **Windows VM** and observe that the ping requests should begin timing out.
7. Once verified, return to the **Linux VM** NSG and **delete the ICMP Deny rule** to restore connectivity.
8. On Powershell, press **Ctrl + C** to stop the pereptual ping.



<p>
<img src="https://imgur.com/vzhjzj9.png" height="90%" width="90%" alt="Blocking ICMP Traffic">
</p>


<br>
<br>

## Step 5️⃣: Observing SSH Traffic

> 📌 *Why?* Observing SSH traffic highlights the importance of encrypted communication when remotely managing servers.

1. In **Wireshark**, apply a filter for `ssh`.
2. On the **Windows 10 VM**, open **PowerShell** and connect to the **Linux VM** using:  ssh *linuxUsername*@*Linux Private IP*
3. **If** prompted, type `yes` to continue, then enter the **Linux VM password** to establish the connection.
4. Once connected, run:  uname -a (to retrieve Linux OS details. Observe the SSH traffic in Wireshark that appears from this command.)
5. Click on any SSH packet in Wireshark; the payload will appear encrypted, demonstrating secure communication because of SSH.




<br>

<p>
<img src="https://imgur.com/0eT2p0c.png" height="120%" width="120%" alt="SSH Traffic">
</p>

