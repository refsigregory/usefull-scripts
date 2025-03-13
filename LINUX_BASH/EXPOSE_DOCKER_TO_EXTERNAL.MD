I had the same issue (although my 22.04 was upgraded from 20.04). The symptoms were exactly the same so I share the solution here, maybe it helps someone. I tried reinstalling docker, as suggested here, but it didn't work. Reinstalling the server was not an option.

In the end, the issue was related to a bug with iptables-nft and snap (also reported to docker-snap):

    Software that manipulates the firewall outside of the configured symlinks (or using iptables-legacy/iptables 1.6 while nftables is also in use) might introduce problems if they are not aware of the xtables/netfilter incompatibility. Eg, this might happen with snaps that ship their own iptables or nftables and unconditionally use it without considering existing rules on the system. [...] The 'docker' snap as of 20.10.12 in the stable channel is known to unconditionally use xtables. At the time of this filing, it did not have a way to adjust to using netfilter, so if using the docker snap, you might have to update your system to use iptables-legacy (on Debian/Ubuntu, see update-alternatives, above).

I found that /etc/alternatives/iptables was pointing to /usr/sbin/iptables-nft, but I also had iptables-legacy rules. See:


```
$ sudo iptables -S
# Warning: iptables-legacy tables present, use iptables-legacy to see them
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
...
$ sudo iptables-legacy -S
-P INPUT ACCEPT
-P FORWARD DROP
-P OUTPUT ACCEPT
...
```


After discovering this, the solution was simply:


`sudo iptables-legacy -P FORWARD ACCEPT`

