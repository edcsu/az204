# view Poswershell version
```ps
    #view version
    $PSVersionTable.PSVersion 
```
# Set Poswershell execution policy
```ps
    #PowerShell script execution policy must be set to remote signed or less restrictive. 
    #Get-ExecutionPolicy -List can be used to determine the current execution policy. 
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
# Install NuGet provider if not available
```ps
    #NuGet provider is required to continue
    #PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories.
    Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force -Scope CurrentUser
```

# Install Az module 
```ps
    Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```

# Azure login
```ps
    Connect-AzAccount -SubscriptionName 'your_account' 
```
# Ensure correct subscription
```ps
    Set-AzContext -SubscriptionName 'your_account'
```
# Create resource group
```ps
    New-AzResourceGroup -Name 'psdemo-rg' -Location "CentralUS"
```

# create credential variables
```ps
$username = 'demoadmin'
$password = ConvertTo-SecureString 'password123$*#@9' -AsPlainText -Force
$WindowsCred = New-Object System.Management.Automation.PSCredential($username, $password)
```

# create vm
```ps
New-AzVm `
    -ResourceGroupName 'psdemo-rg' `
    -Name 'psdemo-win-az' `
    -Image 'Win2019Datacenter' `
    -Credential $WindowCred `
    -OpenPorts 3389
```

# Get public ip addresses
```ps
    Get-AzPublicIpAddress `
    -ResourceGroupName 'psdemo-rg' `
    -Name 'psdemo-win-az' | Select-Object IpAddress
```