Network-sec-groups

In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, IPCONFIG, DNS, DHCP, ICMP)
- Wireshark (Protocol Analyzer)
<h2>Operating Systems Used </h2>
- Windows 10 (21H2)
- Ubuntu Server 20.04

Part 1 (Create our Resources)
Create a Resource Group
Create a Windows 10 Virtual Machine (VM)
While creating the VM, select the previously created Resource Group
While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
Create a Linux (Ubuntu) VM
While create the VM, select the previously created Resource Group and Vnet
Observe Your Virtual Network within Network Watcher

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/43ac0f2e-784e-4477-b60f-32aebddcf2ea)



Part 2 (Observe ICMP Traffic)
Use Remote Desktop to connect to your Windows 10 Virtual Machine
Within your Windows 10 Virtual Machine, Install Wireshark
Open Wireshark and filter for ICMP traffic only
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
Observe ping requests and replies within WireShark
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark


![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/edc2ff2b-083d-4b2a-b0dd-f906d9803f2c)

Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/7675221e-057c-4c60-94cf-2c74fd20f5c3)

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/8311d054-412e-4a99-824a-e81e77b116e9)

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/01f086da-59ff-4407-bdd3-370057b69728)

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/052d341d-d0a0-4473-b6d0-3028c01f8274)


Part 2 (Observe SSH Traffic)
Back in Wireshark, filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter]


![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/9b2e9afa-ed1f-49c9-b4d9-022548047fc0)

Part 2 (Observe DHCP Traffic)
Back in Wireshark, filter for DHCP traffic only
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/898fe139-daf9-44cc-90c3-d00829567b98)

Part 2 (Observe DNS Traffic)
Back in Wireshark, filter for DNS traffic only
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark

![image](https://github.com/Tomcruztech/Network-sec-groups/assets/160645953/eba380a9-665a-4754-82c7-3b4b91bff091)




