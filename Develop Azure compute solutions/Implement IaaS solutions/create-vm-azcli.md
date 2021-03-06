# azure cli

## login interactively and set subscription
```sh
    az login
    az account set --subscription "write_your_subscription"
```

## list resource group
```sh
    az group list --output table 
``` 

## create resource group
```sh
    az group create --name "psdemo-rg" --location "centralus" 
``` 

## create vm 
### windows
```sh
    az vm create \
        --resource-group "psdemo-rg" \
        --name "psdemo-win-cli" \
        --image "win2019datacenter" \
        --admin-username "demoadmin" \
        --admin-password "demo$2#4@5*98d" \
        --public-ip-sku "Basic"  
``` 

### linux
```sh
    az vm create \
        --resource-group "psdemo-rg" \
        --name "psdemo-linux-cli" \
        --image "ubuntults" \
        --admin-username "demoadmin" \
        --authentication-type "ssh" \
        --ssh-key-value ~/.ssh/id_rsa.pub \
        --public-ip-sku "Basic"  
```

```sh
    az vm create \
        --resource-group "psdemo-g" \
        --name "psdemo-linux-cli" \
        --image "ubuntults" \
        --admin-username "demoadmin" \
        --authentication-type "ssh" \
        --generate-ssh-keys \
        --public-ip-sku "Basic"  

```

## open vm port

### windows
```sh
    az vm open-port \
    --resource-group "psdemo-rg" \
    --name "psdemo-win-cli" \
    --port "3389"
```
### linux
```sh
    az vm open-port \
    --resource-group "psdemo-rg" \
    --name "psdemo-linux-cli" \
    --port "22"
```

## list ip addresses

### windows
```sh
    az vm list-ip-addresses \
    --resource-group "psdemo-rg" \
    --name "psdemo-win-cli" \
```

### linux
```sh
    az vm list-ip-addresses \
    --resource-group "psdemo-rg" \
    --name "psdemo-linux-cli" \
```
## delete resource group
```sh
    az group delete --name "psdemo-rg"
```