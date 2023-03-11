
```toc
```

## Interacting with ARM

Azure Resource Manager is the primary way of interacting with Azure Services and Resources.
- ARM REST APIs
- Azure Portal (incl mobile app)
- Azure PowerShell
- Azure CLI
- Azure SDKs

## Common VM Operations

### Start/Stop
Use deallocate instead of shutting down guest or you will continue to incur runtime charges.
Can restart but will get new IP and temp (D) disk
Auto shutdown can be configured

### Resize
Resize - vertical scaling (RAM, CPU, etc.) - requires reboot

### Remove
- VM Resource and its dependencies (virtual NIC, IP, OS and data disks, etc.)
- Resource Group (if represents a single machine and its assets ONLY)
- Taxonomic tags
- Azure PowerShell or CLI
	- allow you to keep OS and/or data disks while deleting config and other resources

### Azure VM Extensions

Extends OS - Requires Azure VM Agent (Windows Server or Linux)
	- Marketplace images have these preinstalled
	- P2V need to have it installed

- Requires VM Access (backdoor - reset admin password, RDP, ssh config)
- VM Backup Extension
- Custom Script (Bash, PowerShell / PowerShell DSC, Puppet, Chef)
- MS Monitoring Agent - onboard into log analytics / Azure Management solutions
	- formerly OMS (Operations Management Suite)

## Procedure
- Open Azure Cloud PowerShell
- Prompted to create storage account first time
- Can 'cd' and 'dir' your way through all Azure resources in your subscription
- Actually in a Docker container
```PowerShell
cd ~
Get-CloudDrive   # See where cloud drive is located
get-azurermvm    # Shows VMs but not which are running or not
get-command AzureRMVM*   # Shows commands
start-azurermvm -name dc1 -ResourceGroupName PowerShellSaturday
stop-azurermvm -name dc1 -ResourceGroupName PowerShellSaturday -Force
```

