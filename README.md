# openwrt-munin-node
openwrt-oriented munin-node implementation inspired by muninlite

## Quick installation guide
Install `munin-node`:
``
mkdir -p /usr/local/bin /etc/munin-node
cd /etc/munin-node
wget -O munin-node.tar.gz https://github.com/MaffC/openwrt-munin-node/archive/master.tar.gz
tar xzf munin-node.tar.gz plugins.d
tar xzf munin-node.tar.gz xinetd-munin-node.conf
tar xzf munin-node.tar.gz munin-node -C /usr/local/bin/
rm munin-node.tar.gz
``

Install dependencies for included plugins as needed (note xinetd is not a plugin dependency and is needed for general operation unless you have another inetd):
``
opkg update
opkg install perl curl iwinfo xinetd
``
Add munin to your `/etc/services` file (feel free to change the port):
``
vi /etc/services
# add the following line:
munin		4949/tcp
``
Configure, enable and start the inetd server:
``
mv /etc/munin-node/xinetd-munin-node.conf /etc/xinetd.d/munin-node
/etc/init.d/xinetd enable
/etc/init.d/xinetd start
``
