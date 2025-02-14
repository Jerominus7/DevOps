
## Networking  #linux #networking #route 
  
Assigning interfaces to a switch.  
  
**ip link** - shows the eth0 interface  
  
**ip addr add [192.168.1.10/24](http://192.168.1.10/24) dev eth0** - assign the IP to the eth0 interface on Host A  
  
Host A with ipaddr 192.168.1.10 connects to switch 192.168.1.0 and then switch connects to Host B  
  
**ip addr add [192.168.1.11/24](http://192.168.1.11/24) dev eth0** - assign the IP to the eth0 interface on Host B  
  
**ping 192.168.1.11** - ping from 192.168.1.10 to 192.168.1.11 to ensure connectivity  
  
Now imagine we have another network with 192.168.2.10 Host C, switch 192.168.2.0, and Host D with 192.168.2.11  
  
The two switches would then need to have a port mapped to a router, that router would have two IPs, one on each network.  
  
Network 1 would go out to the router mapped to 192.168.1.1 and the Network 2 would connect to the same router on 192.168.2.1 via their switch.  
  
**route** - this command displays the routing configuration/route table  
  
**ip route add [192.168.2.0/24](http://192.168.2.0/24) via 192.168.1.1** - allow connection to the other network via the router, KEEP IN MIND THIS NEEDS TO BE RAN ON ALL HOSTS  
  
**route** - display route information to ensure it works  
  
**ip route add [192.168.1.0/24](http://192.168.1.0/24) via 192.168.2.1** - allow the route from Network 2 to Network 1 via the router at 192.168.2.1  
  
**route** - ensure the route is working  
  
Now lets say we need to add access to the internet, you can add the connection to the internet ([172.217.194.0/24](http://172.217.194.0/24)). You will need to add this to the route.  
  
**ip route add [172.217.194.0/24](http://172.217.194.0/24) via 192.168.2.1** - This allows Network 2 access to this IP via the router at 192.168.2.1  
  
Next we can set the default route for any network, where there is not an entry in the route table already specified. I.e. the devices on the network would all default to  
this route if there is no other entry in the route table.  
  
**ip route add default via 192.168.2.1** - sets this path as the default route, all traffic will go out to this router and then out to the internet  
  
**route** - use route to check the route table to ensure the entry exists  
  
Instead of using the word default, you can also use 0.0.0.0, but they mean the exact same thing.  
  
  
Host A eth0 connects to Host B via eth0, Host B uses eth1 to connect to Host C via Host C eth0. The issue is Host A doesn't know about Host C.  
  
So Host A will need to route to Host C via the Host B connection.  
  
**ip route add [192.168.2.0/24](http://192.168.2.0/24) via 192.168.1.6** - this will tell Host A it can connect to the switch in between Host B and Host C ([192.168.2.0/24](http://192.168.2.0/24))  
  
Now we will need to allow Host C to respond to Host A via the switch.  
  
**ip route add [192.168.1.0/24](http://192.168.1.0/24) via 192.168.2.6** - this will allow Host C to connect to the network switch between Host A and Host B ([192.168.1.0/24](http://192.168.1.0/24)) via the interface and IP on Host B (eth1 192.168.2.6)  
  
Now the Host A can send to Host C, and Host C can send to Host A because they have route entries. The issue now, is that by default, Host B cannot forward packets from its eth0 to eth1.  
  
To fix this add the ip_forward setting that allows eth0 and eth1 to send packets across different interfaces.  
  
**cat /proc/sys/net/ipv4/ip_forward** - the default value is 0 for off, set it to 1 to enable it  
  
The issue here, is that this setting is now only set until a reboot. Once the machine reboots, the setting will default back to 0. To fix this, add it to the sysctl.conf file.  
  
**/etc/sysctl.conf** - modify the value for net.ipv4.ip_forward = 0 to net.ipv4.ip_forward = 1