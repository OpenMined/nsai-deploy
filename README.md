[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FOpenMined%2Fnsai-deploy%2Fmain%2Finfra%2Fazuredeploy.json)



# testing
create group
```
az group create \
  --name testResourceGroup \
  --location 'Central US'
```
launch VM
```
az deployment group create \
  --name testSyftboxVM \
  --resource-group testResourceGroup \
  --template-file infra/azuredeploy.json
  ```

  Get ip
  ```
  az vm list-ip-addresses --resource-group testResourceGroup --query "[].{Name:virtualMachine.name, PublicIP:virtualMachine.network.publicIpAddresses[0].ipAddress}" --output table
  ```

  ssh into VM
  ```
  ssh azureuser@<ip>
  ```

  fill in PW Testtest123 (only for demo)

  Cat logs
  ```
  cat /var/log/cloud-init-output.log
  ```


delete group
  ```
  az group delete --name testResourceGroup --yes
  ```