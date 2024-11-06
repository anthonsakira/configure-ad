<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory Deployment in Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>
This project will be a 2 part project. In this 1st part, we will be creating our Virtual Machines (Domain Controller) and (Client). In order to make these we will need to create our Resource Group and Virtual Network and then we will then join them with the Virtual Machines that we will create.
<br />

</p>
<p>
  
 - ***SETTING UP RESOURCE GROUP***
<p> 
<img src="https://i.imgur.com/e5xIVb7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this screenshot, you will see that I numbered the steps in creating the Resource Group. 
<br />
  
<br />
  1) We can search "Resource Group" in the search bar for a quick find.
<br />
  2) We must name our Resource Group and select the proper region for your area.
<br />
  3) Press "Review + Create" on the bottom left corner
<br />
  
Now, once the validation has passed and you see a green check mark we can now press "Create" once again
</p>
<br />

-  ***SETTING UP VIRTUAL NETWORK*** 
<p>
<img src="https://i.imgur.com/GJmUy4S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we move on to creating our Virtual Network. In the Basics tab, we need to set our resource group into the one we just made previously.
Then, we will be naming our virtual network "Active-Directory-VNet". After we're done configuring the names and region, we can press "Review + Create". 

  We can ignore all the other tabs in this case.
<br />
  
***NOTE***    YOU WILL NEED TO HAVE THE SAME REGION SET FOR EVERY VIRTUAL MACHINES YOU MAKE 

</p>
<p>
<br />  

  - ***SETTING UP VIRTUAL MACHINE (DOMAIN CONTROLLER)***
<p> 
<p>
<img src="https://i.imgur.com/TJ71Wxo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the virtual network and resource groups have been deployed, we will now start creating our Virtual Machine (Domain Controller).
  <br />  - In this step, make sure when you create the virtual machine, click the first option from the drop-down menu.
</p>
<br />
<img src="https://i.imgur.com/2B6EsQS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
In the Basics tab, make sure we choose "Active-Directory-Lab" for our Resource Group.

Then, we can name our virtual machine "dc-1" which is our Domain Controller. 
Again, we have to make sure that our region is the same as our virtual network and resource group to avoid errors.
<p>
After that we can scroll down to "Image" and we need to choose 
<p>
  
   ***Windows Server 2022 Datacenter: Azure Edition x64 Gen2***

<p>
<img src="https://i.imgur.com/8M3vI1N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

After choosing the image, we can scroll down to "Size" and choose anything that has "2 vcpus and 8 gb memory".
Now, under Administrator account we can change our Username and Password.
In this case, we will be using ***labuser*** for username and ***Cyberlab123!*** for our password.

<p>
<img src="https://i.imgur.com/sjE05cf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

After those steps, we can now go to the next page 
Basics --> Disk --> Networking 
</p>
Under the Networking tab, we can choose the Virtual Network that we created previously which was "Active-Directory-VNet".
<p>
When done, press "Review+Create".
<p>
If errors occur, please double check the steps listed above and compare settings.
<p>
Once the validation has passed we can select "Create" once again.

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>






















