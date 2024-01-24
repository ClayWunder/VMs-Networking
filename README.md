<p align="center">
  
![image](https://github.com/ClayWunder/VMs-Networking/assets/157168474/4724c3fd-1e82-484f-b4ef-065153d7903b)


</p>

<h1>Deploying and Neworking Virtual Machines (Azure)</h1>

This tutorial outlines the creation and networking of different types of virtual machines (VM's) in Microsoft Azure.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Azure (Network Security Groups)
- Remote Desktop
- Wireshark
- Windows Powershell 

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Linux (Ubuntu)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Resources
- Step 1 - Observe ICMP Traffic
- Step 2 - Observe SSH Traffic
- Step 3 - Observe DHCP Traffic
- Step 4 - Observe DNS Traffic
- Step 5 - Observe RDP Traffic
- Cleanup

<h2>Deployment and Configuration Steps</h2>

<p>
  
![image](https://github.com/ClayWunder/VMs-Networking/assets/157168474/34ff4cae-2483-494f-89f2-855789a64caf)

>
</p>
<p>
Create Resource Group in desired subscription for project in Azure. 
</p>
<br />

<p>
  
![Screenshot 2024-01-23 at 2 54 50 PM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/40740923-8618-4a5e-9438-f8c37112e3d9)

</p>
<p>
Select Virtual Machines from Azure Service Menu
</p>
<br />

<p>
  
![Screenshot 2024-01-23 at 2 58 02 PM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/0bcea8a8-ea4e-4f16-a618-9f8be0f7b65e)

</p>
<p>
Create new virtual machine running Microsoft Windows 10. Place in newly created resource group (same region). VM will create new Virtual Network (VNet) and Subnet.
</p>
<br />

![Screenshot 2024-01-23 at 3 07 16 PM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/77bc3435-ab6a-4980-81f5-3eed3417dd59)

</p>
<p>
VM1 created and appears in Virtual Machine tab of Azure.
</p>
<br />

![Screenshot 2024-01-23 at 3 16 56 PM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/7ba4ba04-9c1c-45b7-a03b-7258b48253b0)

</p>
<p>
Create 2nd Virtual Machine running Linux (Ubuntu) on same Vnet as VM running Windows.
</p>
<br />

![Screenshot 2024-01-23 at 3 19 49 PM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/f9160176-e2fc-40ed-9f4c-010d533cc4b5)

</p>
<p>
Both Virtual Machines now appear in Azure.
</p>
<br />

<h1>Part 1 - Observe ICMP Traffic (Internet Control Message Protocol - no port used)</h1>

<img width="854" alt="Screenshot 2024-01-23 at 3 26 24 PM" src="https://github.com/ClayWunder/VMs-Networking/assets/157168474/c18e52c4-d6e6-4705-9bdc-e5c1dd9e74f7">

</p>
<p>
Use Microsoft Remote Desktop application to connect to Windows 10 virtual machine using it's public IP address and username/password assigned during VM creation.
</p>
<br />

<img width="1484" alt="Screenshot 2024-01-23 at 3 28 41 PM" src="https://github.com/ClayWunder/VMs-Networking/assets/157168474/ed8c83fa-ab2d-4b83-9c3d-bb73223121d0">

</p>
<p>
Download and install Wireshark on Windows 10 virtual machine.
</p>
<br />

<img width="754" alt="Screenshot 2024-01-23 at 3 33 03 PM" src="https://github.com/ClayWunder/VMs-Networking/assets/157168474/e305d5b9-fa20-4d00-aa6f-ec5a45122eca">

</p>
<p>
Run Wireshark and add filter to view ICMP traffic only.
</p>
<br />

![Screenshot 2024-01-24 at 10 45 58 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/10ed090e-9eaa-4292-bde0-5b26420926a2)

</p>
<p>
Copy the private IP address of VM2 running Ubuntu.
</p>
<br />

![Screenshot 2024-01-24 at 10 48 51 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/211a801c-27ff-4f36-aafb-ba6cd1faca73)

</p>
<p>
Return to VM1 and use Windows PowerShell (or Terminal) to ping VM2's private IP address.
Observe ICMP traffic between VM1 (10.0.0.4) and VM2 (10.0.0.5) in Wireshark. 
</p>
<br />

![Screenshot 2024-01-24 at 10 58 33 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/bd04b6b3-8d78-4132-a3fd-11a6ddc9c5e1)

</p>
<p>
Attempt to ping a public website (www.microsoft.com) from PowerShell on VM1 and observe network traffic in Wireshark.
Observe ICMP traffic betweeen VM1 (10.0.0.4) and Microsoft Public IP (23.200.61.123).
</p>
<br />

![Screenshot 2024-01-24 at 11 01 22 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/397d2fce-b78b-42b0-8c07-92aea9c6cb74)

</p>
<p>
Initiate non-stop ping from VM1 to VM2.
</p>
<br />

![Screenshot 2024-01-24 at 11 03 40 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/4491ceab-f4b0-4c03-bb8e-2c6d11ea1558)

</p>
<p>
Return to Azure. Use Network Security Group in VM2 to disable inbound ICMP Traffic, making sure the new rule's priority level is lower than any other currently existing rule.
</p>
<br />

![Screenshot 2024-01-24 at 11 06 58 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/83aa362a-d49b-4919-82e8-15decf583ba3)

</p>
<p>
Observe the ICMP traffic stop in PowerShell and Wireshark.
</p>
<br />

![Screenshot 2024-01-24 at 11 09 23 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/ca7d39cb-5af5-4720-8207-28129d3ac5a8)

</p>
<p>
Return to Azure and change the newly created Network Security Group rule from "deny" to "allow".
</p>
<br />

![Screenshot 2024-01-24 at 11 11 45 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/02b066d3-ed79-4d16-87b9-4cc914c5cf5d)

</p>
<p>
Observe the ICMP traffic resume in PowerShell and Wireshark.
</p>
<br />

</p>
<p>
Stop ping activity by pressing Ctrl + C in PowerShell.
</p>
<br />

<h1>Part 2 - Observe SSH Traffic (Secure Shell - TC Port 22)</h1>

![Screenshot 2024-01-24 at 11 16 04 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/11e7ce91-54ba-425e-811b-48e437417995)

</p>
<p>
Return to Wireshark and filter to view SSH traffic only.
</p>
<br />

![Screenshot 2024-01-24 at 11 18 14 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/5e613aec-1dc5-4ee5-9419-a663a23542bd)

</p>
<p>
SSH (instead of ping) VM2's private IP address. Observe SSH traffic in Wireshark.
Exit SSH connection by pressing typing "exit" in PowerShell and pressing Enter.
</p>
<br />

<h1>Part 3 - Observe DHCP Traffic (Dynamic Host Configuration Protocol - UDP Port 67 & 68)</h1>

![Screenshot 2024-01-24 at 11 23 28 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/3ae384b5-94f1-4794-ac64-cf69320aa5a5)

</p>
<p>
Return to Wireshark and filter to view DHCP traffic only.
</p>
<br />

![Screenshot 2024-01-24 at 11 16 04 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/11e7ce91-54ba-425e-811b-48e437417995)

</p>
<p>
From VM1, use command ipconfig / renew in PowerShell to attempt to issue VM a new IP address.
</p>
<br />

![Screenshot 2024-01-24 at 11 25 02 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/a858995e-f8e6-4e73-a55a-9795bd68bef1)

</p>
<p>
Observe DHCP traffic in Wireshark.
</p>
<br />

<h1>Part 4 - Observe DNS Traffic (Domain Name System - TCP/UDP Port 53)</h1>

![Screenshot 2024-01-24 at 11 16 04 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/11e7ce91-54ba-425e-811b-48e437417995)

</p>
<p>
Return to Wireshark and filter to view DNS traffic only.
</p>
<br />

![Screenshot 2024-01-24 at 11 33 09 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/f13648f3-ef1c-472e-8827-cb9a1087570e)

</p>
<p>
From VM1, use commmand nslookup microsoft.com to see associated public IP address. Observe DNS traffic in Wireshark.
</p>
<br />

<h1>Part 5 - Observe RDP Traffic (Remore Desktop Protocol - TCP Port 3389)</h1>

![Screenshot 2024-01-24 at 11 36 02 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/8692aa2f-0657-4427-902e-d95b168959df)

</p>
<p>
Return to Wireshark and filter to view RDP traffic only.
</p>
<br />

![Screenshot 2024-01-24 at 11 37 38 AM](https://github.com/ClayWunder/VMs-Networking/assets/157168474/a6a28b35-cc41-4fb1-83cd-f73fcc036130)

</p>
<p>
Observe RDP traffic in Wireshark. Activity will be non-stop since remote desktop is currently use and traffic is constantly being transmitted.
</p>
<br />

<h1>Cleanup</h1>

</p>
<p>
Close remote desktop connection and delete resource groups in Azure. This will ensure charges for bandwidth and the operation of virtual machines will stop.
</p>
<br />

