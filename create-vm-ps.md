# Azure login
```ps
    Connect-AzAccount -SubscriptionName 'your_account'
```
# Ensure correct subscription
```ps
    Set-AzContext -SubscriptionName 'your_account'
```

# create credential variables
```ps
$username = 'demoadmin'
$password = 'password123$*#@9' -AsPlainText -Force
$WindowsCred = New-Object System.Management.Automation.PSCredentail($username, $password)
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