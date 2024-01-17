# AzureVnet
Deployed a network security group and also configured web application firewalls as well as created a virtual network with application security groups and network security groups.
https://clipchamp.com/watch/Fj84oTEmcdD

Made with Clipchamp <iframe allow="autoplay;" allowfullscreen style="border:none" src="https://clipchamp.com/watch/Fj84oTEmcdD/embed" width="640" height="360"></iframe>
>>>>>> I FOLLOWED THE FOLLOWING STEPS BELOW TO CREATE MY HOME LAB VNET <<<<<<

Task 1 - Create a virtual network

From the Azure portal menu, select + Create a resource > Networking > Virtual network, or search for Virtual Network in the portal search box.

Select Create.

On the Basics tab of Create virtual network, enter or select this information:

Expand table

Setting

Value

Project details

Subscription

Select your subscription.

Resource group

Select Create new. Enter myResourceGroup. Select OK.

Instance details

Name

Enter myVNet.

Region

Select East US.

Select the Review + create tab, or select the blue Review + create button at the bottom of the page.

Select Create.

Task 2 - Create an application security group

 Note

An application security group (ASG) enables you to group together servers with similar functions, such as web servers.

From the Azure portal menu, select + Create a resource > Networking > Application security group, or search for Application security group in the portal search box.

Select Create.

On the Basics tab of Create an application security group, enter or select this information:

Expand table

Setting

Value

Project details

Subscription

Select your subscription.

Resource group

Select myResourceGroup.

Instance details

Name

Enter myAsgWebServers.

Region

Select (US) East US.

Select the Review + create tab, or select the blue Review + create button at the bottom of the page.

Select Create.

 Note

Repeat the previous steps, specifying the following values:

Expand table

Setting

Value

Project details

Subscription

Select your subscription.

Resource group

Select myResourceGroup.

Instance details

Name

Enter myAsgMgmtServers.

Region

Select (US) East US.

Select the Review + create tab, or select the blue Review + create button at the bottom of the page.

Select Create.

Task 3 - Create a network security group

From the Azure portal menu, select + Create a resource > Networking > Network security group, or search for Network security group in the portal search box.

Select Create.

On the Basics tab of Create network security group, enter or select this information:

Expand table

Setting

Value

Project details

Subscription

Select your subscription.

Resource group

Select myResourceGroup.

Instance details

Name

Enter myNSG.

Location

Select (US) East US.

Select the Review + create tab, or select the blue Review + create button at the bottom of the page.

Select Create.

Task 4 - Associate network security group to subnet

Search for myNsg in the portal search box.

Select Subnets from the Settings section of myNSG.

In the Subnets page, select + Associate:

Under Associate subnet, select myVNet for Virtual network.

Select default for Subnet, and then select OK.

Task 5 - Create security rules

Select Inbound security rules from the Settings section of myNSG.

In Inbound security rules page, select + Add:

Create a security rule that allows ports 80 and 443 to the myAsgWebServers application security group. In Add inbound security rule page, enter or select this information:

Expand table

Setting

Value

Source

Leave the default of Any.

Source port ranges

Leave the default of (*).

Destination

Select Application security group.

Destination application security groups

Select myAsgWebServers.

Service

Leave the default of Custom.

Destination port ranges

Enter 80,443.

Protocol

Select TCP.

Action

Leave the default of Allow.

Priority

Leave the default of 100.

Name

Enter Allow-Web-All.

Select Add.

Complete steps 3-4 again using this information:

Expand table

Setting

Value

Source

Leave the default of Any.

Source port ranges

Leave the default of (*).

Destination

Select Application security group.

Destination application security group

Select myAsgMgmtServers.

Service

Leave the default of Custom.

Destination port ranges

Enter 3389.

Protocol

Select Any.

Action

Leave the default of Allow.

Priority

Leave the default of 110.

Name

Enter Allow-RDP-All.

Select Add.

 Caution

Remote Desktop Protocol (port 3389) is exposed to the internet for the VM that is assigned to the myAsgMgmtServers application security group. For production environments, instead of exposing port 3389 to the internet, it's recommended that you connect to Azure resources that you want to manage using a VPN, private network connection, or Azure Bastion.

Task 6 - Create virtual machines

From the Azure portal menu, select + Create a resource > Compute > Virtual machine, or search for Virtual machine in the portal search box.

In Create a virtual machine, enter or select this information in the Basics tab:

Expand table

Setting

Value

Project details

Subscription

Select your subscription.

Resource group

Select myResourceGroup.

Instance details

Virtual machine name

Enter myVMWeb.

Region

Select (US) East US.

Availability options

Leave the default of No infrastructure redundancy required.

Security type

Leave the default of Standard.

Image

Select Windows Server 2019 Datacenter - Gen2.

Azure Spot instance

Leave the default of unchecked.

Size

Select Standard_D2s_V3.

Administrator account

Username

Enter a username.

Password

Enter a password.

Confirm password

Reenter password.

Inbound port rules

Select inbound ports

Select None.

Select the Networking tab.

In the Networking tab, enter or select the following information:

Expand table

Setting

Value

Network interface

Virtual network

Select myVNet.

Subnet

Select default (10.0.0.0/24).

Public IP

Leave the default of a new public IP.

NIC network security group

Select None.

Select the Review + create tab, or select the blue Review + create button at the bottom of the page.

Select Create. The VM may take a few minutes to deploy.

Create the second virtual machine

 Note

Complete steps 1-6 again, but in step 2, enter myVMMgmt for Virtual machine name. Wait for the VMs to complete deployment before advancing to the next section.

Associate network interfaces to an Application Security Group

 Note

When you created the VMs, Azure created a network interface for each VM, and attached it to the VM.

Add the network interface of each VM to one of the application security groups you created previously:

Search for myVMWeb in the portal search box.

Select Networking from the Settings section of myVMWeb VM.

Select the Application security groups tab, then select Configure the application security groups.

In Configure the application security groups, select myAsgWebServers. Select Save.

 Note

Complete steps 1 and 2 again, searching for the myVMMgmt virtual machine and selecting the myAsgMgmtServers ASG.

Task 7 - Test traffic filters

Search for myVMMgmt in the portal search box.

On the Overview page, select the Connect button and then select RDP.

Select Download RDP file.

Open the downloaded rdp file and select Connect. Enter the username and password you specified when creating the VM.

Select OK.

You may receive a certificate warning during the connection process. If you receive the warning, select Yes or Continue, to continue with the connection.

The connection succeeds, because inbound traffic from the internet to the myAsgMgmtServers application security group is allowed through port 3389.





https://clipchamp.com/watch/Fj84oTEmcdD


<div style="position:relative;width:fit-content;height:fit-content;">
            <a style="position:absolute;top:20px;right:1rem;opacity:0.8;" href="https://clipchamp.com/watch/Fj84oTEmcdD?utm_source=embed&utm_medium=embed&utm_campaign=watch">
                <img loading="lazy" style="height:22px;" src="https://clipchamp.com/e.svg" alt="Made with Clipchamp" />
            </a>
            <iframe allow="autoplay;" allowfullscreen style="border:none" src="https://clipchamp.com/watch/Fj84oTEmcdD/embed" width="640" height="360"></iframe>
        </div>
