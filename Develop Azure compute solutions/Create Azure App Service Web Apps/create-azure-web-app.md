# In the Cloud Shell, create a directory and then navigate to it.
```sh
    mkdir htmlapp

    cd htmlapp
```

# Clone the sample app repository to your htmlapp directory.
```sh
    git clone https://github.com/Azure-Samples/html-docs-hello-world.git
```

# Create the webapp.
```sh
    cd html-docs-hello-world

    az webapp up --location <myLocation> --name <myAppName> --html
```

# Redeploy the app with the same.
```sh
    az webapp up --location <myLocation> --name <myAppName> --html
```

# Clean up resources.
```sh
    az group delete --name <resource_group> --no-wait
```

