# openwrt-munin-node
openwrt-oriented munin-node implementation inspired by muninlite

## Quick installation guide
Install `munin-node` and the bundled plugins:

```
opkg update
opkg install curl
mkdir -p /usr/local/bin /etc/munin-node
cd /etc/munin-node
curl -Lko munin-node.tar.gz https://github.com/MaffC/openwrt-munin-node/archive/master.tar.gz
tar xzf munin-node.tar.gz openwrt-munin-node-master/plugins.d
tar xzf munin-node.tar.gz openwrt-munin-node-master/xinetd-munin-node.conf
tar xzf munin-node.tar.gz openwrt-munin-node-master/munin-node -C /usr/local/bin/
rm munin-node.tar.gz
```

Install dependencies for included plugins as needed (note xinetd is not a plugin dependency and is needed for general operation unless you have another inetd; curl is a plugin dependency but is installed if you follow the above quick installation guide):

```
opkg update
opkg install perl curl iwinfo xinetd
```

Add munin to your `/etc/services` file (feel free to change the port):

```
vi /etc/services
# add the following line:
munin		4949/tcp
```

Configure, enable and start the inetd server:

```
mv /etc/munin-node/xinetd-munin-node.conf /etc/xinetd.d/munin-node
/etc/init.d/xinetd enable
/etc/init.d/xinetd start
```
