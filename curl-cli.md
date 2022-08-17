## Get Site Certificate Expiration Date

```Shell
curl -vI "https://$domain" 2>&1 | grep -o 'expire date: .*$'
```
