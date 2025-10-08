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
In this phase, the Windows Server 2022 VM is promoted to a Domain Controller and configured with Active Directory Domain Services.  
This allows centralised management of users and security policies for the network domain.

