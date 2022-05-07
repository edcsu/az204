# AZ CLI
## create resource group
```sh
    az group create -n webapps-dev-rg -l westus2
```

## create service plan
```sh
    az appservice plan create --name webapps-dev-plan \
    --resource-group webapps-dev-rg \
    --sku s1 \
    --is-linux
```

## create web app
```sh
    az webapp create -g webapps-dev-rg \
    -p webapps-dev-plan \
    -n mp10344884 \
    --runtime "node|10.14"
```

## delete resource group
```sh
    az group delete -n webapps-dev-rg
```

# AZ Powershell
## Replace the following URL with a public GitHub repo URL
```ps1
    $webappname="mywebapp$(Get-Random)"
    $location="West Europe"
    $myResourceGroup="webapp-dev-rg"
```

## Create a resource group.
```ps1
    New-AzResourceGroup -Name $myResourceGroup -Location $location
```

## Create an App Service plan in Free tier.
```ps1
    New-AzAppServicePlan -Name $webappname -Location $location -ResourceGroupName $myResourceGroup -Tier Free
```

## Create a web app.
```ps1
    New-AzWebApp -Name $webappname -Location $location -AppServicePlan $webappname -ResourceGroupName myResourceGroup
```

## Configure GitHub deployment from your GitHub repo and deploy once.
```ps1
    $PropertiesObject = @{
        repoUrl = "$gitrepo";
        branch = "master";
        isManualIntegration = "true";
    }
    Set-AzResource -Properties $PropertiesObject -ResourceGroupName myResourceGroup -ResourceType Microsoft.Web/sites/sourcecontrols -ResourceName $webappname/web -ApiVersion 2015-08-01 -Force
```

## delete resource group
```ps1
    Remove-AzResourceGroup -Name myResourceGroup -Force
```