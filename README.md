# Create a Resource Group
Azure resources are organized into resource groups. Create a resource group:
```bash
az group create --name request-logger --location canadacentral
```
# Create a Storage Account
```bash
az storage account create --name requestlogger2024 --location canadacentral --resource-group request-logger --sku Standard_LRS
```
# Create an Azure Function App
```bash
az functionapp create --resource-group request-logger --consumption-plan-location canadacentral --runtime dotnet --functions-version 4 --name requestlogger2024 --storage-account requestlogger2024
```
