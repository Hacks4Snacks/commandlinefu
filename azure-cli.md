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
