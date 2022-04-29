## Set NOPASSWD for sudo user

```Shell
echo "$USER ALL=(ALL) NOPASSWD:ALL" | sudo EDITOR="tee -a" visudo
```

## Disable IPv6 Ubuntu

```Shell
sudo sed -i '$a\net.ipv6.conf.all.disable_ipv6=1 \
net.ipv6.conf.default.disable_ipv6=1 \
net.ipv6.conf.lo.disable_ipv6=1' /etc/sysctl.conf \
&& sudo sysctl -p
```
