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
## Add Column with value to file

```Shell
awk 'BEGIN{ FS = OFS = "|" } { print $0, (NR==1? "COLUMNNAME" : "ROWVALUE") }' <SOURCEFILENAME> > tmp && mv tmp <SOURCEFILENAME>
```

## Remove characters from specific column with defined output seperator

```Shell
awk -F'|' 'BEGIN { OFS = "|"}{ gsub(/\abcd/,"", $5); print } ' <SOURCEFILE> > <TARGETFILE>
```

## View memory usage of an application or process

```Shell
ps -eo size,pid,user,command --sort -size | awk '{ sz=$1/1024 ; printf("%13.2f MB ",sz) } { for ( x=4 ; x<=NF ; x++ ) { printf("%s ",$x) } print "" }' | cut -d "" -f2 | cut -d "-" -f1 | grep <PROCESSNAME> | awk '{ SUM += $1} END { print SUM }'
```