
# create resource group
```sh
    az group create -n webapps-dev-rg -l westus2
```

# create service plan
```sh
    az appservice plan create --name webapps-dev-plan \
    --resource-group webapps-dev-rg \
    --sku s1 \
    --is-linux
```

# create web app
```sh
    az webapp create -g webapps-dev-rg \
    -p webapps-dev-plan \
    -n mp10344884 \
    --runtime "node|10.14"
```

# delete resource group
```sh
    az group delete -n webapps-dev-rg
```