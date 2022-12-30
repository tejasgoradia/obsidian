
# Azure Resource Manager (ARM) Template

The following sections is sourced from [# Comparing JSON and Bicep for templates](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/compare-template-syntax) 

## Template Schema
```json
"$schema":"<Location of the JSON schema file that describes the version of the template language. Use the URL shown in the preceding example>",
"contentVersion":"<Version of the template (such as 1.0.0.0)>",
"parameters":{<Values that are provided when deployment is executed to customize resource deployment>},
"variables":{<Values that are used as JSON fragments in the template to simplify template language expressions>},
"functions":[<User-defined functions that are available within the template>],
"resources":[<Resource types that are deployed or updated in a resource group>],
"outputs":{<Values that are returned after deployment>}
```

## Expressions
```json
To author an expression:
"[func()]"
```

## Parameters
```json
To declare a parameter with a default value
"parameters": {
  "orgName": {
    "type": "string",
    "defaultValue": "Contoso"
  }
}

To get a parameter value, use the name you defined:
"name": "[parameters('orgName'))]"
```

## Variables
```json
To declare a variable:To declare a variable:
"variables": {
  "description": "example value"
},

To get a variable value, use the name you defined:
"workloadSetting": "[variables('description'))]"
```

## Strings
```json
To concatenate strings:
"name": "[concat(parameters('namePrefix'), '-vm')]"
```

## Logical operators
```json
To return the logical **AND**:
[and(parameter('isMonday'), parameter('isNovember'))]

To conditionally set a value:
[if(parameters('isMonday'), 'valueIfTrue', 'valueIfFalse')]
```
## Deployment scope
```json
To set the target scope of the deployment:
"$schema": "https://schema.management.azure.com/schemas/2018-05-01/subscriptionDeploymentTemplate.json#"
```
## Resources
```json
To declare a resource:
"resources": [
  {
    "type": "Microsoft.Compute/virtualMachines",
    "apiVersion": "2020-06-01",
    ...
  }
]

To conditionally deploy a resource:
"resources": [
  {
    "condition": "[parameters('deployVM')]",
    "type": "Microsoft.Compute/virtualMachines",
    "apiVersion": "2020-06-01",
    ...
  }
]

To set a resource property:
"sku": "2016-Datacenter",

To get the resource ID of a resource in the template:
[resourceId('Microsoft.Network/networkInterfaces', variables('nic1Name'))]
```

## Loops
```json
To iterate over items in an array or count:
"copy": {
  "name": "storagecopy",
  "count": "[length(parameters('storageAccountNames'))]"
},
...
```

## Resource dependencies
```json
If you must set an explicit dependence, use:
"dependsOn": ["[resourceId('Microsoft.Storage/storageAccounts', 'parameters('storageAccountName'))]"]
```

## Reference resources
```json
To get a property from a resource in the template:
[reference(resourceId('Microsoft.Storage/storageAccounts', variables('storageAccountName'))).primaryEndpoints.blob]

[reference(resourceId('Microsoft.Network/virtualNetworks/subnets', variables('subnetName'))).properties.addressPrefix]

To get a property from an existing resource that isn't deployed in the template:
// required every time the property is needed
"[reference(resourceId('Microsoft.Storage/storageAccounts/', parameters('storageAccountName')), '2019-06-01').primaryEndpoints.blob]"
```

## Outputs
```json
To output a property from a resource in the template:
"outputs": {
  "hostname": {
    "type": "string",
    "value": "[reference(resourceId('Microsoft.Network/publicIPAddresses', variables('publicIPAddressName'))).dnsSettings.fqdn]"
  },
}

To conditionally output a value:
"outputs": {
  "hostname": {
    "condition": "[variables('condition')]",
    "type": "string",
    "value": "[reference(resourceId('Microsoft.Network/publicIPAddresses', variables('publicIPAddressName'))).dnsSettings.fqdn]"
  }
}
```

# Powershell techniques

## Variables
```bash
$loc = "East US"
New-AzResourceGroup -Name "MyResourceGroup" -Location $loc
```
## Loops
```bash
# -lt for "less than", -le for "less than or equal", -eq for "equal", -ne for not equal"
For ($i = 1; $i -lt 3; $i++)
{
    $i
}
```
## Parameters
```bash
# provide names for each parameter to help the script extract the values
.\setupEnvironment.ps1 -size 5 -location "East US"

# capture the values into variables
param([string]$location, [int]$size)
```