# AzureDocker

curl -sL http://aka.ms/InstallAzureCLIDeb | sudo bash

- create group
rgname=sd-webapp
az group create -n $rgname -l japaneast

- Azure make plan
appservicename=linux-plan
az appservice plan create --name $appservicename --resource-group $rgname --sku B1 --is-linux

- webapp up
webappname=sd-webapp-$RANDOM-zip
az webapp up --name $webappname --resource-group $rgname --plan $appservicename

- delete app
az group delete --name $rgname



- Azure INSIGHTS
https://docs.microsoft.com/ja-jp/azure/azure-monitor/app/nodejs

export APP_INSIGHTS_KEY="XXXX-XXXX-XXXX-XXXX"
az webapp config appsettings set -g $rgname -n $webappname --setting APP_INSIGHTS_KEY="xxxxxxxx"

az webapp stop -g $rgname -n $webappname
az webapp start -g $rgname -n $webappname