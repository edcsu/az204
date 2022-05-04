# create credential variables
```ps
$username = 'demoadmin'
$password = 'password123$*#@9'
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