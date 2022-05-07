```sh
    ACR_LOGINSERVER = $(az acr show --name $ACR_NAME --query loginServer --output tsv)

    az container create \
        --resource-group psdemo-rg \
        --name psdemo-webapp-cli \
        --dns-name-label psdemo-webapp-cli \
        --ports 80 \
        --image $ACR_LOGINSERVER/webappimage:v1 \
        --registry-login-server $ACR_LOGINSERVER
        --registry-username $SP_APPID 
        --registry-password $SP_PASSWD
```