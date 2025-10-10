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

After the restart, logged in as **ADLAB\Administrator** via Remote Desktop to access the admin account of the domain.

Verification of Installation:
Server Manager -> Tools -> Active Directory Users and Computers

Here, adlab.local dropdown with users is visible, verifying the installation.

   <img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/65025abc-a99a-4d1b-a40f-b08b3a3b69dd" />




