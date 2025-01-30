<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Step 1: Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Step 2: Within your Windows 10 Virtual Machine, Install the WireShak application
- Step 3: Ping the Ubuntu Virtual Machine to observe ICMP traffic, disable and re-enable ICMP traffic through the Network Security Group
- Step 4: Observe SSH traffic on the Windows Virtual Machine
- Step 5: Observe DNS traffic on the Windows Virtual Machine
- Step 6: Observe RDP traffic on the Windows Virtual Machine
- Step 7: Clean up by deleting the resource groups to ensure we don't incur any charges

<h2>Actions and Observations</h2>

![Screenshot 2025-01-29 195414](https://github.com/user-attachments/assets/7430437c-ff10-4d70-981e-c1a03c334fed)

![Screenshot 2025-01-29 195612](https://github.com/user-attachments/assets/33772f21-6c22-471d-99ab-a8059dc58a5a)

![Screenshot 2025-01-29 195735](https://github.com/user-attachments/assets/656ba319-22a7-46f8-b018-7c02b58f4e6f)

![Screenshot 2025-01-29 195914](https://github.com/user-attachments/assets/8d093ac3-ab04-47db-b2d0-10ef5be13197)

![Screenshot 2025-01-29 200102](https://github.com/user-attachments/assets/819445c0-3dfc-4f43-8bf8-342ab116fb03)


<p>
First, enter the Azure portal by going to https://portal.azure.com/. 

After you enter the portal, go to you Windows VM and copy the public IP address. We will be connecting to this VM by Remote Desktop Connection. To find RDC, type it into the Windows search bar it will be the first selection. A pop up will show up where you will put the public IP address of the VM to connect. After pressing connect, you'll need to use the username and password we created to log in and then pressing OK.
</p>
<br />

![Screenshot 2025-01-29 200350](https://github.com/user-attachments/assets/45396727-b432-4e68-b1ab-8839e5318bc6)

<p>
Check everything to no in the privacy settings when the VM finally loads up.
</p>
<br />

![Screenshot 2025-01-29 200610](https://github.com/user-attachments/assets/95d6b744-8a38-4b8d-a57a-857c8359e358)


<p>
In the VM, go to the EDGE browser and download Wireshark. You can copy and paste this link (https://www.wireshark.org/download.html). You will need to download the Windows Installer (64-bit)
</p>
<br />

![Screenshot 2025-01-29 200824](https://github.com/user-attachments/assets/b93748ca-d9b2-4e80-bcf2-99b7132a22f4)

![Screenshot 2025-01-29 200901](https://github.com/user-attachments/assets/adf1077f-3e71-46d4-8793-5b30c6cd27b2)

![Screenshot 2025-01-29 200917](https://github.com/user-attachments/assets/0ad59320-ecb0-43a6-b556-74323269e911)

![Screenshot 2025-01-29 201102](https://github.com/user-attachments/assets/e3091274-37af-4264-ace6-06b39554b97c)

![Screenshot 2025-01-29 201141](https://github.com/user-attachments/assets/96127d2f-2ad8-4836-97ba-4a9d5f170b1c)

![Screenshot 2025-01-29 201202](https://github.com/user-attachments/assets/28cc6078-b766-46a5-b72b-2d4e11a314a8)

![Screenshot 2025-01-29 201253](https://github.com/user-attachments/assets/90799fa9-83ad-4b01-8d60-4289634d52c1)

![Screenshot 2025-01-29 201329](https://github.com/user-attachments/assets/5d4fcecc-edfa-4b48-ad26-3d93ef73c0a4)

![Screenshot 2025-01-29 201410](https://github.com/user-attachments/assets/31258ec1-30d4-47c1-83f4-f5234dfa467f)

![Screenshot 2025-01-29 201456](https://github.com/user-attachments/assets/2ad3d89f-eda6-4cb9-8d27-be9fe7d4b332)

![Screenshot 2025-01-29 201741](https://github.com/user-attachments/assets/cc85d688-f2ee-48eb-a8b1-652d380f0ce0)

![Screenshot 2025-01-29 201826](https://github.com/user-attachments/assets/a17dced2-eb4b-473c-aaf6-00d1b290485d)

<p>
Open the installer and install everything to the default settings by pressing "Next" all the way to the end.
</p>
<br />

<p>
<img src="https://i.imgur.com/xLbHAtN.png"/>
</p>
<p>
When Wireshark is open, filter by "icmp" packets and hit the blue shark fin to start capturing traffic through the VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/4fxurLf.png"/>
</p>
<p>
Find your Ubuntu VM's private IP and copy it.
</p>
<br />

<p>
<img src="https://i.imgur.com/paiFYqT.png"/>
</p>
<p>
Head back to your VM and open cmd or powershell through the Windows search bar in the bottom left. You will now ping -t the private IP address of the Unbuntu VM to make a continuous ICMP traffic that you can observe through Wireshark. We should see requests from Ubuntu VM's private IP and replies from our Windows private IP.
</p>
<br />

<p>
<img src="https://i.imgur.com/RbC2bZL.png"/>
</p>
<p>
We are going to disable ICMP traffic from the Ubuntu virtual machine's network security group in the Azure portal. To get to the NSG page, type in "NSG" in search bar and click onto the service.
</p>
<br />

<p>
<img src="https://i.imgur.com/2ZVWZBr.png"/>
</p>
<p>
Find the NSG for the Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/KXUwodG.png"/>
</p>
<p>
After you are on the NSG page, click on "Inbound security rules".
</p>
<br />

<p>
<img src="https://i.imgur.com/kqS58Sw.png"/>
</p>
<p>
Add a new rule with ICMP as the protocol and set the action to deny. We must change the priority to a number that is lower than the first rule in the list. The lower number allows the rule to have a higher priority than the other rules that have a higher number. In this tutorial, I set it to 200 as it has a higher priority than 300.
</p>
<br />

<p>
<img src="https://i.imgur.com/qSAu6wS.png"/>
</p>
<p>
After applying the rule, head back into the VM and observe how the ping to the private IP address will time out or fail.
</p>
<br />

<p>
<img src="https://i.imgur.com/ZFaMu0f.png"/>
</p>
<p>
Now we will select allow on the rule and the traffic should now continue through.
</p>
<br />

<p>
<img src="https://i.imgur.com/NK9QreR.png"/>
</p>
<p>
After applying the rule, we should now see traffic continue on the VM again!
</p>
<br />

<p>
<img src="https://i.imgur.com/dJxpVHL.png"/>
</p>
<p>
We have now observed ICMP traffic through RDC between two VMs and will now connect to the Ubuntu VM via SSH or Secure Shell within the command lines of PowerShell. Firstly, you will need to type "SSH (your Ubuntu private IP address). When prompted with 
  
  "The authenticity of host '10.0.0.5 (10.0.0.5)' can't be established.
ECDSA key fingerprint is SHA256:wYAdmAbrJ/JTv69D9C8feZvkyQAHgpvW5ZNdt2AvYfA.
Are you sure you want to continue connecting (yes/no/[fingerprint])?"
 
  Type "Yes"

  After continuing, it will ask for a password. This is the password that we set when we made the VM so type it in. The password will be invisible when typing so just be aware that it is still typing even though it may not look like it.
</p>
<br />

<p>
<img src="https://i.imgur.com/qwZ0w8l.png"/>
</p>
<p>
In wireshark, filter the traffic by "ssh" without saving.
</p>
<br />

<p>
<img src="https://i.imgur.com/lm3cnCf.png"/>
</p>
<p>
In the SSH connection, type in the command line linux shell commands or anything in general to see the SSH traffic. Afterwards, type "exit" to disconnect from SSH
</p>
<br />

<p>
<img src="https://i.imgur.com/wRHQB9w.png"/>
<img src="https://i.imgur.com/NFOD1JZ.png"/>
<img src="https://i.imgur.com/rjfTLR5.png"/>
</p>
<p>
 
We will now observe DHCP traffic through our VM.
  
Back in wireshark, filter by "DHCP" and refresh. In the command line, type in "ipconfig /renew" to give the Windows VM a new IP address. This proccess will use the DHCP protocol and can be observed on wireshark.
  
Afterwards, we can observe DNS traffic by typing in the command line "nslookup google.com" or any other website to see the traffic and changing the filter in Wireshark to "DNS". Lastly, we will be able to observe the constant RDP traffic by either typing it into the filter or "tcp.port == 3389" in Wireshark. This will conclude this tutorial and we will now delete the resource groups to avoid any costs.
</p>
<br />

<p>
<img src="https://i.imgur.com/TZXjAuP.png"/>
</p>
<p>
To delete the resource group, just go back to the resource groups page, click on the resource group, click delete resource group, and type/copy paste the resource group's name to confirm, and then click delete.
