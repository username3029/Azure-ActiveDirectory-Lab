# Azure Active Directory Lab
A homelab project for simulating a small network in Azure using Windows Server 2025 and Windows 11 clients
## Environments and Technologies Used
- Microsoft Azure
- Active Directory Domain Services
- PowerShell
- Remote Desktop
## Operating Systems Used
- Windows Server 2025
- Windows 11


## VM Configurations
1. Created a new resource group: **ActiveDirectoryLab group**  
2. Selected Windows Server 2022 Datacenter (Desktop Experience) from Azure Marketplace  
3. Chose region **Australia East**  
4. Configured VM size **Standard_D2s_v3**  
5. Enabled **RDP (3389)** for remote access  
6. Verified configuration and deployed the VM

I begin by establishing a connection using Remote Desktop to the virtual machine

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/376f9d97-e3ab-4a45-9dd1-fd7188fa98ab" />

## Active Directory Domain Services (AD DS) Setup
In this phase, the Windows Server 2025 VM is promoted to a Domain Controller and configured with Active Directory Domain Services.  
This allows centralised management of users and security policies for the network domain.

Steps taken:
1. Server Manager -> Add Roles and Features
2. Left Installation Type, Server Selection Settings, Add Features Section as Default
3. Ensured **Active Directory Domain Services** is selected in **Server Roles**
4. Proceeded to Install

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/0fa18097-e65f-4818-bc82-58dc7f6fe9fe" />

The next step is to promote the server to domain controller.

Steps taken :
1. In add roles and features wizard, **Promote this server to a domain controller** option was selecten.
2. Selected **“Add a new forest”**  
3. In this simulated lab, the name 'adlab.local' was chosen.
4. Kept **DNS** and **Global Catalog (GC)** selected.
5. Set a **DSRM password** 
7. Retained default settings for subsequent options and proceeded to install.

Verification of Installation:
Server Manager -> Tools -> Active Directory Users and Computers

Here, adlab.local dropdown with users is visible, verifying the installation.T

   <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/65025abc-a99a-4d1b-a40f-b08b3a3b69dd" />

Following, I created a new organisational unit titled 'employees'.
I create two new users in this container: John Smith & Alice Davis

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/104dc4de-dfd6-48ff-acbb-fb8c5226d4fd" 

 ## Connecting an Employee’s Computer (Windows 11 Client VM) 

For this step, a Windows 10 client VM was created in Azure.

First, I check the Azure Portal to note down the private IP address of the server VM in the networking section (10.0.0.4)

Control Panel > Network and Sharing Center > Change adapter settings > Select active adapter (in this case, ethernet) > Properties.
Here, the preferred DNS was set to Private IP of the domain controller.

<img width="400" height="700" alt="image" src="https://github.com/user-attachments/assets/b702d81c-601f-4d35-b25c-dda18dba2d07" />

To join the client VM to the adlab.local domain, the domain membership was changed through the **computer name** section in **system properties**

<img width="400" height="700" alt="image" src="https://github.com/user-attachments/assets/56c001d5-76dc-4c60-af13-2217b62551e6" />

Since client user accounts can only be accessed via Remote Desktop (on cloud VM), users jsmith & adavis were given remote desktop access privileges via the **remote** section of **System Properties**.
Now, John Smith's account can be accessed and a fully functioning Azure AD Homelab has been set up.

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/d0c8d376-44ce-4b3e-b926-4f1e8f22b31e" />














