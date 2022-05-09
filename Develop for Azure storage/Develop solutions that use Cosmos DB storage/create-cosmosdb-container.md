# Azure CLI

## create a sql api cosmos db account
```sh
    az cosmosdb create --name pluralsight --resource-group pluralsight
```
## create a sql database
```sh
    az cosmosdb sql database create --account-name pluralsight --name sampledb
```

## create a sql database container
```sh
    az cosmosdb sql container create --resource-group pluralsight \
    --account-name pluralsight \ 
    --database-name sampledb \
    --name samplecontainer \ 
    --partition-key-path “/employeeid”
```
