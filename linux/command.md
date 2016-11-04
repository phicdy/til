## Install deb file

```bash
dpkg -i file.deb
```

## Check port

### CentOS 7

netstat was deprecated. Use 'ss' command, but it has a bug about udp.

http://d.hatena.ne.jp/ozuma/20140915/1410774381

#### Option 

* -n, --numeric       don't resolve service names
* -a, --all           display all sockets
* -p, --processes     show process using socket
* -t, --tcp           display only TCP sockets
* -u, --udp           display only UDP sockets

#### tcp

```bash
ss -antp
```

#### udp

```bash
ss -anup
```
