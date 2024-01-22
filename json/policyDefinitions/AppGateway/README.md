# No network peering to ER network

No network peering can be associated to networks in network in a resource group containing central managed network infrastructure.

## Try on Portal

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-policy%2Fmaster%2Fsamples%2FNetwork%2Fno-network-peerings-to-er-network%2Fazurepolicy.json)

## Try with PowerShell

````powershell
$definition = New-AzPolicyDefinition -Name "app-gateways-must-be-zone-redundant" -DisplayName "Application Gateways must be Zone Redundant" -description "Application Gateways can be configured to be either Zone Aligned, Zone Redundant, or neither. Application Gateways that have exactly one entry in their zones array are considered Zone Aligned. In contrast, Application Gateways with 3 or more entries in their zones array and a capacity of at least 3 are recognized as Zone Redundant. This policy helps identify and enforce these resilience configurations." -Policy 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Network/no-network-peerings-to-er-network/azurepolicy.rules.json' -Parameter 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Network/no-network-peerings-to-er-network/azurepolicy.parameters.json' -Mode All
$definition
$assignment = New-AzPolicyAssignment -Name <assignmentname> -Scope <scope>  -resourceGroupName <ER Network Resource Group Name> -PolicyDefinition $definition
$assignment 
````



## Try with CLI

````cli

az policy definition create --name 'app-gateways-must-be-zone-redundant' --display-name 'Application Gateways must be Zone Redundant' --description 'Application Gateways can be configured to be either Zone Aligned, Zone Redundant, or neither. Application Gateways that have exactly one entry in their zones array are considered Zone Aligned. In contrast, Application Gateways with 3 or more entries in their zones array and a capacity of at least 3 are recognized as Zone Redundant. This policy helps identify and enforce these resilience configurations.' --rules 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Network/no-network-peerings-to-er-network/azurepolicy.rules.json' --params 'https://raw.githubusercontent.com/Azure/azure-policy/master/samples/Network/no-network-peerings-to-er-network/azurepolicy.parameters.json' --mode All

az policy assignment create --name <assignmentname> --scope <scope> --policy "no-network-peerings-to-er-network" 

````