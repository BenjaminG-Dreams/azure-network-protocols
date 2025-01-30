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

![Screenshot 2025-01-29 202848](https://github.com/user-attachments/assets/d4645c87-e31d-471b-b922-de52f9e9c76f)
![Screenshot 2025-01-29 203136](https://github.com/user-attachments/assets/0d629c0b-4f22-417b-87f5-77c81531df12)

<p>
When Wireshark is open, filter by "icmp" packets and hit the blue shark fin to start capturing traffic through the VM.
</p>
<br />

![Screenshot 2025-01-29 203403](https://github.com/user-attachments/assets/4d6458e4-47b9-4e1c-bd1c-5eb32503a131)

<p>
Find your Ubuntu VM's private IP and copy it.
</p>
<br />

![Screenshot 2025-01-29 203653](https://github.com/user-attachments/assets/3c492338-fc38-463b-a577-e4ae7bc1e448)

![Screenshot 2025-01-29 203904](https://github.com/user-attachments/assets/b4fcf8f3-c0e4-4e3b-8ac6-571412151887)

![Screenshot 2025-01-29 205250](https://github.com/user-attachments/assets/f0e17bb3-2744-4a56-94c7-8b8e86b2ec8c)

<p>
Head back to your VM and open cmd or powershell through the Windows search bar in the bottom left. You will now ping -t the private IP address of the Unbuntu VM to make a continuous ICMP traffic that you can observe through Wireshark. We should see requests from Ubuntu VM's private IP and replies from our Windows private IP.
</p>
<br />

![Screenshot 2025-01-29 204610](https://github.com/user-attachments/assets/f3612eb4-f1aa-4eac-a9df-83872b9fb7b4)

![Screenshot 2025-01-29 204951](https://github.com/user-attachments/assets/e6b9f4c7-52fe-4bdc-879d-b2e55edfeb26)


<p>
We are going to disable ICMP traffic from the Ubuntu virtual machine's network security group in the Azure portal. To get to the NSG page, type in "NSG" in search bar and click onto the service.
</p>
<br />


![Screenshot 2025-01-29 204434](https://github.com/user-attachments/assets/f3ba82be-038c-47b8-89ad-5a5164a58a57)

![Screenshot 2025-01-29 204447](https://github.com/user-attachments/assets/758e5c88-7332-4597-a785-4a961a0927b5)

<p>
Find the NSG for the Ubuntu VM.
</p>
<br />

![Screenshot 2025-01-29 204610](https://github.com/user-attachments/assets/fca25ec6-058e-44b8-8af3-f71609cb41a9)

<p>
After you are on the NSG page, click on "Inbound security rules".
</p>
<br />

![Screenshot 2025-01-29 204951](https://github.com/user-attachments/assets/c9d68328-0aa2-4e98-8bee-3fbe7d7436a6)

<p>
Add a new rule with ICMP as the protocol and set the action to deny. We must change the priority to a number that is lower than the first rule in the list. The lower number allows the rule to have a higher priority than the other rules that have a higher number. In this tutorial, I set it to 200 as it has a higher priority than 300.
</p>
<br />

![Screenshot 2025-01-29 205630](https://github.com/user-attachments/assets/5797152e-0743-447d-85f4-59b3979d0afa)

<p>
After applying the rule, head back into the VM and observe how the ping to the private IP address will time out or fail.
</p>
<br />

![Screenshot 2025-01-29 205722](https://github.com/user-attachments/assets/81cab519-0dcf-4d0a-ac11-17c862d5111a)

<p>
Now we will select allow on the rule and the traffic should now continue through.
</p>
<br />

![Screenshot 2025-01-29 210643](https://github.com/user-attachments/assets/6a02b026-d100-464c-85fb-4c7438c4e47e)

<p>
After applying the rule, we should now see traffic continue on the VM again!
</p>
<br />

![Screenshot 2025-01-29 210643](https://github.com/user-attachments/assets/99e5367b-fa06-4ed5-a5c0-573ed1d7f4f0)
![Screenshot 2025-01-29 210859](https://github.com/user-attachments/assets/7b10c3bd-c26e-4664-845c-cb904c771c4d)

<p>
We have now observed ICMP traffic through RDC between two VMs and will now connect to the Ubuntu VM via SSH or Secure Shell within the command lines of PowerShell. Firstly, you will need to type "SSH (your Ubuntu private IP address). When prompted with 
  
  "The authenticity of host '10.1.0.5 (10.1.0.5)' can't be established.
ECDSA key fingerprint is SHA256:wYAdmAbrJ/JTv69D9C8feZvkyQAHgpvW5ZNdt2AvYfA.
Are you sure you want to continue connecting (yes/no/[fingerprint])?"
 
  Type "Yes"

  After continuing, it will ask for a password. This is the password that we set when we made the VM so type it in. The password will be invisible when typing so just be aware that it is still typing even though it may not look like it.
</p>
<br />

![Screenshot 2025-01-29 210643](https://github.com/user-attachments/assets/5eb855a6-a4a6-4d3c-8e67-3122d1c2561f)

<p>
In wireshark, filter the traffic by "ssh" without saving.
</p>
<br />

![Screenshot 2025-01-29 211407](https://github.com/user-attachments/assets/c7081865-925c-46b0-bb17-56832f810781)

![Screenshot 2025-01-29 211524](https://github.com/user-attachments/assets/daa10cd0-f194-42c1-a0c8-c6193b24a9ef)

![Screenshot 2025-01-29 211608](https://github.com/user-attachments/assets/f60e8b38-a655-4976-a2ab-9a4c4d91fd6d)

<p>
In the SSH connection, type in the command line linux shell commands or anything in general to see the SSH traffic. Afterwards, type "exit" to disconnect from SSH
</p>
<br />

![Screenshot 2025-01-29 211838](https://github.com/user-attachments/assets/df6a00b6-0f33-4870-809c-d71ed2ca87bb)

![Screenshot 2025-01-29 212013](https://github.com/user-attachments/assets/6a94cfc4-ae4e-488d-999d-5d7d4e6a9f36)

<p>
 
We will now observe DHCP traffic through our VM.
  
Back in wireshark, filter by "DHCP" and refresh. In the command line, type in "ipconfig /renew" to give the Windows VM a new IP address. This proccess will use the DHCP protocol and can be observed on wireshark.
</p>
<br />

![Screenshot 2025-01-29 212140](https://github.com/user-attachments/assets/71858dc4-08ec-4879-aa84-853dd1b91f77)
![Screenshot 2025-01-29 212535](https://github.com/user-attachments/assets/f4d6155b-18b9-4982-a83b-3021c92a2f11)

 <p> 
Afterwards, we can observe DNS traffic by typing in the command line "nslookup disney.com" or any other website to see the traffic and changing the filter in Wireshark to "DNS".
</p>
<br />

![Screenshot 2025-01-29 212922](https://github.com/user-attachments/assets/e8fae04b-6f40-46e4-bc13-d4f86b5561a6)

 <p> 
Lastly, we will be able to observe the constant RDP traffic by either typing it into the filter or "tcp.port == 3389" in Wireshark. This will conclude this tutorial and we will now delete the resource groups to avoid any costs.
</p>
<br />

![Screenshot 2025-01-29 213110](https://github.com/user-attachments/assets/5bf969f4-c6f5-4815-9099-d3aabdf04333)

<p>
To delete the resource group, just go back to the resource groups page, click on the resource group, click delete resource group, and type/copy paste the resource group's name to confirm, and then click delete.
