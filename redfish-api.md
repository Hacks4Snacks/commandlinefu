## View iDRAC HTTPS Certificates

```Shell
curl -sku ${USERCREDS} https://<bmcip>/redfish/v1/Managers/iDRAC.Embedded.1/NetworkProtocol/HTTPS/Certificates/SecurityCertificate.1 | jq
```

## View BIOS Settings

```Shell
curl -sku ${USERCREDS} https://<bmcip>/redfish/v1/Systems/System.Embedded.1 | jq
```

## View SecureBoot Status

```Shell
curl -sku ${USERCREDS} https://<bmcip>/redfish/v1/Systems/System.Embedded.1/SecureBoot | jq
```

## Enable SecureBoot

```Shell
curl -X PATCH -k -H "Content-Type: application/json" -H "If-Match:*" -u ${USERCREDS} https://<bmcip>/redfish/v1/Systems/Self/SecureBoot -d '{"SecureBootEnable": true}' | jq
```

## View Scheduled Jobs

```Shell
curl -sku ${USERCREDS} https://<bmcip>/redfish/v1/Managers/iDRAC.Embedded.1/Jobs | jq
```

## Delete a Scheduled Job

```Shell
 curl -X DELETE -sku ${USERCREDS} https://<bmcip>/redfish/v1/Managers/iDRAC.Embedded.1/Jobs/<JID> | jq
```