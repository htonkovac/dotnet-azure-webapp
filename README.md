# dotnet-azure-webapp
This codebase can be run in azure as a demo app


## Recreate repo steps
1. dotnet new webapp -n MyFirstAzureWebApp2
2. vim web.config

## Deploy to azure with autoswap
```
zip -r deploy.zip .
az webapp config appsettings set  --settings WEBSITE_RUN_FROM_PACKAGE="1" --name testappsvc12345 --resource-group app-svc-test --slot cicdslot
az webapp deployment slot auto-swap  --name testappsvc12345 --slot cicdslot --resource-group app-svc-test
az webapp deployment source config-zip --src deploy.zip --name testappsvc12345 --slot cicdslot --resource-group app-svc-test
```

alternatively - manually swap
```
az webapp deployment slot swap  --name testappsvc12345 --slot cicdslot --resource-group app-svc-test --target-slot production
```
