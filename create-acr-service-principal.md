## create azure container registry 
```sh
    ACR_NAME='psdemoacr'
    ACR_REGISTRY_ID = $(az acr show --name $ACR_NAME --query id --output tsv)
    
    SP_NAME='acr-service-principal'
    SP_PASSWORD = $(az acr create \
        --name http://$ACR_NAME-pull \
        --scopes $ACR_REGISTRY_ID \
        --role acrpull \
        --query id \
        --output tsv) 

    SP_APPID = $(az ad sp show \
        --id http://$ACR_NAME-pull \
        --query appId \
        --output tsv)  
``` 