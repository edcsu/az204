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


## create azure container registry 
```sh
    ACR_NAME='psdemoacr'
    az acr create \
        --resource-group psdemo-rg \
        --name $ACR_NAME \
        --sku Standard  
``` 

## login into ACR to push containers
```sh
    az login $ACR_NAME
```

## get loginserver used in the name tag
```sh
    ACR_LOGINSERVER = $(az acr show --name $ACR_NAME --query loginServer --output tsv)
```

## tag image using login server name
```sh
    docker tag webappimage:v1 $ACR_LOGINSERVER/webappimage:v1
    docker image ls $ACR_LOGINSERVER/webappimage:v1
    docker image ls
```

## push image to acr
```sh
    docker push $ACR_LOGINSERVER/webappimage:v1
```

## get list of repos and images\tags in acr
```sh
    az acr repository list --name $ACR_NAME --output table
    az acr repository show-tags --name $ACR_NAME --repository webappimage --output table
```


# ACR tasks
```sh
    az build --image "webappimage:v1-acr-task" --registry $ACR_NAME .
```