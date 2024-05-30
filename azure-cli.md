## Get list of Azure accounts

```Shell
az account list --output table
```

## Set active Azure account

```Shell
az account set --subscription-id <SUBSCRIPTION-ID>
```

## Get account access token

```Shell
az account get-access-token --query accessToken --output tsv
```

## Execute REST command against resource

```Shell
token=$(az account get-access-token --query accessToken --output tsv)
az rest --method get --url <RESOURCE URL> --headers "{\"Authorization\": \"Bearer $token\"}" -o json
```

## Create CBL-Mariner VM

```Shell
az vm create --name <NAMEOFVM> --resource-group <NAMEOFRESOURCEGROUP>  --admin-username <ADMINUSERNAME> --ssh-key-values <PATHTOPUBSSHKEY> --image MicrosoftCBLMariner:cbl-mariner:cbl-mariner-2:latest --os-disk-size-gb <OSDISKSIZE>
```

## Run Nexus Read Command

```Shell
az networkcloud baremetalmachine run-read-command --commands arguments=<ARGUMENT> command=<COMMAND> --ids <RESOURCEID> --limit-time-seconds=60 --verbose --debug
```

## Run Nexus Run Command

```Shell
az networkcloud baremetalmachine run-command --ids <RESOURCEID> --limit-time-seconds=60 --verbose --debug --script <BASE64ENCODEDSCRIPT>
```

## Get OAM IP Addresses of Nexus Baremetal Machines

```Shell
az networkcloud baremetalmachine list --resource-group <RESOURCEGROUP> | jq -r '.[] | {machineName: .machineName, oamip: .oamIpv4Address}'
```

## Get Latest Extension Version (Requires extension registration in active subscription)

```Shell
az k8s-extension extension-types list-versions-by-location --location <REGION> --extension-type <EXTENSIONNAME> --show-latest 2>/dev/null | jq -r '.[0].properties.version'
```