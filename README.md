<p align="center">
  
![image](https://github.com/ClayWunder/VMs-Networking/assets/157168474/4724c3fd-1e82-484f-b4ef-065153d7903b)


</p>

<h1>Deploying and Neworking Virtual Machines (Azure)</h1>

This tutorial outlines the creation and networking of different types of virtual machines (VM's) in Microsoft Azure.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Wireshark
- 

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Linux (Ubuntu)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Create Resources
- Step 2 - Observe ICMP Traffic
- Step 3 - Observe SSH Traffic
- Step 4 - Observe DHCP Traffic
- Step 5 - Observe RDP Traffic

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
Create new virtual machine running Microsoft Windows 10 in project resource group and region. VM will create new Virtual Network (VNet) and Subnet.
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

<img width="854" alt="Screenshot 2024-01-23 at 3 26 24 PM" src="https://github.com/ClayWunder/VMs-Networking/assets/157168474/c18e52c4-d6e6-4705-9bdc-e5c1dd9e74f7">

</p>
<p>
Use Microsoft Remote Desktop application to connect to Windows 10 virtual machine using it's public IP address and username/password chosen during VM creation.
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
