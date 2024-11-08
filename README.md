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
  1) We can search "Resource Group" in the search bar for a quick find. Then we click "+Create"
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
<img src="https://i.imgur.com/8fr5GIm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/jPyOnc2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Once it's done deploying and it is up and running, we can go back to Virtual Machines on Azure and we will create another VM which will then be our "Client". 

<p>
<img src="https://i.imgur.com/VnekXaO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

While in "Basics" tab we're going to put our VM inside the same Resource Group that we've been using which is "Active-Directory-Lab" and please make sure it's under the same Region as well.
<p>
For this VM we will be naming it "client-1"

<p>
<img src="https://i.imgur.com/8BAge5F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

We can now scroll down to "Image", "Size" and "Username/PW" and we can choose the following options below.
<p> 
  
  Image: ***Windows 10 Pro, version 22h2 -x64 Gen2***
<p>
  
  Size: ***Standard_D2s_v3 - 2vcpus, 8GiB memory***
<p>
  
  Username: ***labuser***
<p>
  
  Password: ***Cyberlab123!***

<p>
<img src="https://i.imgur.com/y5J37mB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HrkvupE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once you're done with the page you can scroll down to "Licensing" and check the box. (1st Screenshot)
<p>

  ***NOTE***   PLEASE MAKE SURE YOU CHECK THIS BOX UNDER LICENSING OR ELSE YOU WON'T BE ABLE TO CREATE THE VM

After you check the box you can go to the next two tabs called "Networking" make sure the Virtual Network is set to "Active-Directory-VNet" then
we can press "Review+Create) when done. (2nd Screenshot)

<p>
<img src="https://i.imgur.com/hVFuPxd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Once again, when the validation has passed and you got a green check mark and the deployment is done you're good to configure your Domain Controller's NIC Private IP adress to be "Static".
<p>
I will be showing you how in the next few steps.

<p>
<img src="https://i.imgur.com/R7q9UVr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

In order to get here, we must go back to Virtual Machines and then go to "dc-1" which is our domain controller.
After that, you want to click "dc-1" --> Drop-down Networking --> Networking Settings
<p>
You must click the blue highlighted item under "Network interface/Ip configuration" which I underlined red in the picture.

<p>
<img src="https://i.imgur.com/dhsQNVg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Once you click the box you will be redirected to this page. Make sure you're under Settings --> Ip Configurations.
Next, click "ipconfig1" highlighted in blue as shown in the screenshot and a mini page will pop up on the right side of your screen.
<p>
Under "Private IP address settings", change the allocation from "Dynamic" to "Static" then click Save. 
<p>
This will then keep your Private IP address the same no matter how many times you restart it.


<p>
<img src="https://i.imgur.com/iuyO9VO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Now, once we're finished with setting our Private IP address to static we can go back to virtual machines and copy the Public IP address for "dc-1".
<p>
We're going to connect to "Remote Desktop Connection" in the next following steps.

<p>
<img src="https://i.imgur.com/bDtChFI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/83iVTwv.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/dBHUq1M.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

In the pictures above, I showed how you can find "Remote Desktop Connection" for ***WINDOWS OS***. 
<p>
You can search it up on the bottom taskbar on your computer right next to the windows logo.
<p>
Once you see it, click it, it will open a little window which you've seen on the 3RD SCREENSHOT.

<p>
<img src="https://i.imgur.com/dBHUq1M.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/Ki6DFrS.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Once you've copied the Public IP address from "dc-1" you're going to paste it to "Remote Desktop Connection" where it says "Computer"
<p>
Another window will pop up telling you to sign in but before that make sure you click "more choices" >>> "Use a different account".
<p>
  
We're going to sign in with ***"labuser"*** and the password we're using is ***"Cyberlab123!"***

<p>
<img src="https://i.imgur.com/7KOF0wx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
</p>
<p>

If you come across this window after connecting just press "Yes" everytime it comes up.

<p>
<img src="https://i.imgur.com/7CFEl7O.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
</p>
<p>

Once you're connected, this "Server Manager" window should pop up, and if it doesn't, make sure you're using "Windows Server" not "Windows 10 pro". 
<p>
Otherwise, you can re-do the steps above if any errors occur.
<p>
<img src="https://i.imgur.com/fYcoOlb.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
<p>
<img src="https://i.imgur.com/fq7Kpvt.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>

***INSIDE THE VM***
<p>
When you're good to go, we can search "run" on the bottom left and type in "wf.msc" this will bring up "Windows Firewall"

<p>
<img src="https://i.imgur.com/quKy3AG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

Please click the blue highlighted item named "Windows Defender Firewall Properties"
<p>
Next, after pressing the highlighted item a window will pop up and we will switch the "Firewall state" from "On" to "Off"
<p>
Please do the same for the other 2 tabs labeled.
<p>
When done, click apply then press okay.
<p>

  - ***Next, we will set Client-1's DNS settings to DC-1's Private IP address***

<p>
<img src="https://i.imgur.com/6vkCz3i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

First, we have to go back to Azure Virtual Machines on our main computer and we're going to click on ***dc-1***
<p>
Then, in the "Overview" tab under "Networking" we can see our Private IP address which is 10.0.0.4 but this can be different on your end.
<p>
Copy the Private IP address then we will paste it in the following step below.

<p>
<img src=https://i.imgur.com/7qMzSSZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

After copying the Private IP address we can go to the network settings under networking while being in the same page. 
<p>
Then we can click on the highlighted item that is underlined in red.

<p>
<img src="https://i.imgur.com/5Id8Yl1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

Once you click on it, it will direct you to this page make sure that you're in "DNS servers" under settings
<p>
Now we want to change the DNS server from "inherit from virtual network" to "Custom"
<p>
Then, we can paste our Client's Private IP address into the DNS Server Name and then click "Save"

<p>
<img src="https://i.imgur.com/oxtquhS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

After saving it, we can now restart the VM from the Azure portal by checking "client-1" and pressing the "Restart" button

<p>
<img src="https://i.imgur.com/QunI9vX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>
<p>
<img src="https://i.imgur.com/0S2zEFD.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
</p>
<p>
<p>
<img src="https://i.imgur.com/dHZx2Hh.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> 
</p>
<p>

Now, after restarting, we can copy the "Public IP address" of "client-1" and paste it on a different "Remote Desktop Connection" as shown above.
<p>
Again, we will connect to the VM with the same credentials as our "dc-1"
<p>
  
Username: ***labuser***
<p>
  
Password: ***Cyberlab123!***
<p>

<p> 
  
   - Next, We will attempt to ping "dc-1's" Private IP address using "client-1" with ***Powershell***

  
<p>
<img src="https://i.imgur.com/EY8vVVj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

When this window pops up, we can switch them all to "No" otherwise, it doesn't really affect anything.

<p>
<img src="https://i.imgur.com/q6uSgIg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

In order to ping "dc-1" Private IP address, we have to go back to ***Azure portal >>> Virtual Machines >>> dc-1 >>> Private IP address*** 
<p>
  
Please copy the Private IP address and we will paste it on ***Powershell***
<p>
  
  ***NOTE!!! AGAIN, THESE IP ADDRESSES MAY BE DIFFERENT ON YOUR END.***

<p>
<img src="https://i.imgur.com/EKwmRfb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>
<p>
<img src="https://i.imgur.com/SYrWyMg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

A window like this should pop up after clicking the program.
<p>
  
For us to ping "dc-1" we can type ***ping 10.0.0.4*** which in my case, the Private IP address that my VM has.
<p>
Now, the data inside the box proves that we are connected with our domain controller (dc-1)
<p>
If you tried to ping it and you get an error that says "Request Timed Out" it could be because they're in different Virtual Networks or dc-1's Windows Firewall might still be on.
<p> Re-trace the steps if you encounter any of these situations.

<p>
<img src="https://i.imgur.com/Q9vTaqt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

Next, we can type in ***"ipconfig /all"*** and if you look/scroll down the "DNS SERVERS" should be the same as "dc-1's" Private IP address.
<p>
This shows that we are on the right track.

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>
