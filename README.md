# openwrt-munin-node
openwrt-oriented munin-node implementation inspired by muninlite

## Quick installation guide
Install `munin-node`:

`mkdir -p /usr/local/bin /etc/munin-node
cd /etc/munin-node
wget -O munin-node.tar.gz https://github.com/MaffC/openwrt-munin-node/archive/master.tar.gz
tar xzf munin-node.tar.gz plugins.d
tar xzf munin-node.tar.gz munin-node -C /usr/local/bin/
rm munin-node.tar.gz`

Install dependencies for included plugins as needed:

`opkg update
opkg install perl curl iwinfo`
