# Azure Function App Hosted on Dedicated Plan

This sample Azure Resource Manager template deploys an Azure Function App hosted on Dedicated plan and required resource including ZipDeploy extension to mount zip package for deployment.

[![Deploy to Azure](/images/deploytoazure.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure-Samples%2Ffunction-app-arm-templates%2Fmain%2Ffunction-app-dedicated-plan%2Fazuredeploy.json)

### OS

This template has a parameter `functionPlanOS` to choose Windows or Linux OS. Windows is selected by default. If you choose Linux, then parameter `linuxFxVersion` will be required, so you can skip it for Windows.

### Dedicated Plan

The Azure Function app provisioned in this sample uses an [Azure Functions Dedicated plan](https://docs.microsoft.com/en-us/azure/azure-functions/dedicated-plan). 

+ **Microsoft.Web/serverfarms**: The Azure Functions Dedicated plan (a.k.a. App Service plan)

### Azure Function App

The Function App uses the [AzureWebJobsStorage](https://docs.microsoft.com/azure/azure-functions/functions-app-settings#azurewebjobsstorage) and [WEBSITE_CONTENTAZUREFILECONNECTIONSTRING](https://docs.microsoft.com/azure/azure-functions/functions-app-settings#website_contentazurefileconnectionstring) app settings to connect to a Storage Account.

+ **Microsoft.Web/sites**: The function app instance.

### ZipDeploy Extension

The Zip Deploy extension is added along with recommended app setting `WEBSITE_RUN_FROM_PACKAGE=1` to mount the zip package for deployment. This is the recommended path for deployment, except for [Linux Consumption Plan](/function-app-linux-consumption)

+ **Microsoft.Web/sites/extensions**: The ZipDeploy extension.

### Azure Storage account

The Storage account that the Function uses for operation and for file contents. 

+ **Microsoft.Storage/storageAccounts**: [Azure Functions requires a storage account](https://docs.microsoft.com/azure/azure-functions/storage-considerations) for the function app instance.

### Application Insights

[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview) is used to provide [monitor the Azure Function](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

+ **Microsoft.Insights/components**: The Application Insights instance used by the Azure Function for monitoring.
