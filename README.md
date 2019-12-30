# AzureDocker

curl -sL http://aka.ms/InstallAzureCLIDeb | sudo bash

-
rgname=sd-webapp
az group create -n $rgname -l japaneast

- Azure make plan
appservicename=linux-plan
az appservice plan create --name $appservicename --resource-group $rgname --sku B1 --is-linux

-
webappname=sd-webapp-$RANDOM-zip
az webapp up --name $webappname --resource-group $rgname --plan $appservicename

- delete app
az group delete --name $rgname