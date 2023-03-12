## Capture traffic for an interface

```Shell
tcpdump -i {interface}
```

## Capture traffic for an interface and write to file

```Shell
tcpdump -i {interface} -w {file}
```

## Read packets from file and don't resolve host and port

```Shell
tcpdump -r {file} -n
```

## Read packets from file and don't resolve, show as ASCII

```Shell
tcpdump -r file -n -A
```

## Read packets from file, filter on host

```Shell
tcpdump -r {file} 'host {ipaddress}'
```

## Read packets from file, filter on direction and host

```Shell
tcpdump -r {file} 'src host {ipaddress}'
```

## Read packets from file, filter on direction and host using NOT

```Shell
tcpdump -r {file} 'icmp and (src host {ipaddress})'
```