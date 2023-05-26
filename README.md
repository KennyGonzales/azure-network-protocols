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
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Write here  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
  
Write here  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />
