## Set NOPASSWD for sudo user

```Shell
echo "$USER ALL=(ALL) NOPASSWD:ALL" | sudo EDITOR="tee -a" visudo
```
