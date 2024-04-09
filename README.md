### Create a Resource Group
Azure resources are organized into resource groups. Create a resource group:
```bash
az group create --name request-logger --location canadacentral
```
### Create a Storage Account
```bash
az storage account create --name requestlogger2024 --location canadacentral --resource-group request-logger --sku Standard_LRS
```
### Create an Azure Function App
```bash
az functionapp create --resource-group request-logger --consumption-plan-location canadacentral --runtime dotnet --functions-version 4 --name requestlogger2024 --storage-account requestlogger2024
```
### Deploy Your Function App
```bash
func azure functionapp publish MyFunctionApp
```
### Verify Deployment
using curl in bash or cmd
```bash
curl -X POST https://requestlogger2024.azurewebsites.net -d "param1=value1&param2=value2"
```
using powershell
```powershell
$jsonData = Get-Content -Path "C:\path\to\your\payload.json" -Raw | ConvertFrom-Json
Invoke-WebRequest -Uri https://requestlogger2024.azurewebsites.net -Method POST -Body ($jsonData | ConvertTo-Json) -ContentType "application/json"
```
