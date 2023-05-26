<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource Groups 
- Install Wireshark
- Observe Network Protocols

<h2>Actions and Observations</h2>



<p>
  
### **Resources:**
  
To create the Resource Group, you have two options. You can either perform a quick search for "Resource Group" at the top of the Azure portal, or you can select "Create a Resource" and then choose to create the Resource Group from the Azure Marketplace.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
After creating the resource group, select + Create.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Select Subscription, which will be Azure subscription 1, and enter your custom created Resource Group. 
  
Select the preferred region that is nearest to you, which will assist saving on cost in our case.   
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
### **Virtual Machines:**
  
>**Note**: The two virtual machines allows us to send traffic between the two machines. Name the two virtual machines to whatever name you prefer, as long as you can remember its names. 
  
To create the first virtual machine, which will be running the Windows operating system and named VM1, you can perform a quick search at the top of the Azure portal for "Virtual Machine," and then select "Virtual machines" from the search results.
  
Choose + Create, then select "Create a virtual machine hosted by azure" option.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Select the "subscription", same "resource group" (RG-LAB-2), name the virtual machine as VM1, select the same region, and set the image as Windows 10 Pro Version. 
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
>**Note**: Make sure to check the licensing checkbox to avoid encountering an error message during the validation process when creating the virtual machine.
  
Allow port 3389, to remote desktop into the virtual machine later in this lab.   
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Allow the networking and the other settings as default, and select Review. If necessary, review the details that have been selected for this Virtual Machine. Once the details of the settings are in order, click Create. 
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
We will now create Virtual Machine 2 (VM2) with Linux Ubuntu Server, which will be using a ssh public key instead of a password for authentication for remote access. Once you set the remaining parts of the settings as default, click on Review, then Create.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
</p>
<br />

<p>
  
These two Virtual Machines will be used for Remote desktop, and observing different network traffic between the two virtual machines.   
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
### **Wireshark:**
  
By performing a quick search for "remote desktop connection," you will be able to access the VM. Enter the public IP address details of VM1 (Windows 10 21H2) to install Wireshark, a packet analysis software, directly on the VM instead of using your local machine.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
With VM1 (Windows Pro), download Wireshark. 
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
>**Note**: Npcap is the Windows version of the libpcap library which includes a driver to support capturing packets. Wireshark uses this library to capture live network data on Windows.
  
Once Npcap appears, install with defaults. After Wirehsark is installed, do a quick search on the bottom left of the Windows Virtual Machine for Wireshark to open.
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Once you open Wirehsark, click Ethernet. Then, click the blue fin to begin capturing packets. Once finished, you will see the network traffic within the Windows Virtual Machine.   
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
</p>
<br />

<p>
  
### **Network Protocols:**
  
Retrieve the private IP address from VM2, and ping it into VM1. The purpose of the ping command is to test the connection between the virtual machines. 
  
By filtering the ICMP packets in Wireshark, we can view the traffic travel from VM1 to VM2. You have the option to ping other IP addresses or domain names like "www.google.com" using Wireshark. The filtered traffic (ICMP), and the corresponding request and reply can be observed in the captured Wireshark data and the PowerShell output displayed below.
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
</p>
<br />

<p>
  
By adding a rule to the Network Security Group in VM2, we can deny the ping request. As a result, the PowerShell output shows a timeout and Wireshark no longer displays a reply for this request.
  
After configuring the network security group inbound rules to deny ICMP (ping) traffic, both Wireshark and PowerShell show timeouts for the ping requests. The requests are no longer received and are reflected below. 
  
In the Azure portal, search for Network Security Group, and click on VM 2 (Linux Ubuntu Server).
  
To add a new inbound security rule, go to Inbound security rules and click + Add. Tick ICMP under the protocol options and set the action to Deny. Assign a priority before 300 to ensure the rule takes effect before others.
  
>**Note**: Priority increases as the number decreases.
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
After creating the rule, in PowerShell you will see "Request timed out" and Wireshark will only display the ICMP requests.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
To re-enable the rule, you can either delete it from the network security group or select it and choose to allow the rule again.
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
In Wireshark, apply the filter "SSH" or "tcp.port == 22". In PowerShell, use the command "ssh username@ip_address" with the private IP address to log in to the Linux Ubuntu Server.
  
After typing "yes" to confirm the connection, enter the password (note that it won't be displayed). Execute commands like touch, pwd, or ls in the Linux SSH session. WireShark captures SSH traffic. To exit the SSH connection, type "exit" and press Enter.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Filter Wireshark for "DHCP traffic." Execute the command "ipconfig /renew" in VM1 (Windows 10 21H2) to obtain a new IP address. WireShark now captures DHCP traffic.
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Apply a filter in Wireshark to display only DNS traffic. Click the refresh button to clear any existing traffic.
  
Execute the command "nslookup www.disney.com" in PowerShell to retrieve the IP addresses associated with the domain "www.disney.com."  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Filter for RDP traffic (tcp.port == 3389) in Wireshark to exclusively capture the ongoing transmission of live stream data between computers. 
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
To delete the resource group, search for "Resource Group" and select the one containing the two virtual machines (Windows 10 Pro & Linux Ubuntu Server).
  
After selecting the Resource Group, enter the name and choose "Delete" at the top of the page, followed by the final delete button at the bottom.  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

|Terms | Descriptions|
|-------|------------|
|Remote Desktop| Remote desktop enables users to establish a connection with a computer located elsewhere, providing a view of its desktop and allowing interaction as if it were a local machine.
|DHCP| Dynamic Host Configuration Protocol is a network management protocol that automates the process of assigning IP addresses and other communication parameters to devices connected to an IP network. It follows a client-server architecture.
|DNS| Domain Name System converts easily recognizable domain names (such as www.amazon.com) into numerical IP addresses (such as 192.0.2.44) that computers can understand.
|SSH| Secure Shell facilitates secure remote connections between computers, enabling command line access from one system to another.
|RDP| Remote Dekstop Protocol is used when remotely connecting from one computer to another to gain a remote desktop GUI (Graphical User Interface)
|ICMP| Internet Control Message Protocol is a network protocol used for diagnostics and error reporting in IP networks. It allows devices to exchange control messages to verify connectivity, troubleshoot issues, and report errors. ICMP is commonly used with the ping utility to test network host reachability and response time.
