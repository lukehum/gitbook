we have a /48

All VLANs are /64


IPv6 Addressing Architecture

/48 is longest, minimum size prefix advertized on the Internet

some feds using /52 and /53s

2001:0db8:1234:5678::    /64
        /16      /32    /48        
         /20      /36    /52
            /24    /40     /56
               /28   /44     /60


/64 - preferred prefix lenght, support NDP, SLAAC, Stable SLAAC, SEND, and facilitates ease of use. RFC 7421


Legacy /126 Usage
/127 - Efficient, LImits NDP cache exhaustion (RFC 6583) and ping-pong attack (RFC 3627, RFC 6164)

/128 - loopbacks

For Enterprises, just use /64 always except for loopbacks


Alternative to /127 is to give rtr 1, a .0 and rtr 2, a .1.   OR /126 rtr 1, a .1 and rtr 2, a .2. Then limit cache exhausiton.

ipv6 nd cache interface-limit 10 <- this will limit it to only 10 entries, mitigating NDP cache exhaustion

More of an issue for a service provider anyway. 

Likelihood of DDOS attacks for enterprise is low, so don't really worry about it, so just use /64 for everything and add ipv6 nd cache interface-limit.


ipv6 unicast-routing
ipv6 cef
show ipv6 cef <ipv6_dest_addr>
show ipv6 cef summary
show mls cef summary

debug ipv6 cef



ipv6 route ::/0 <next-hop-IPv6-address>

Link Local Address is a valid next hop, each VLAN can have a fe80::1

under int vlan 11
ipv6 address FE80::1 link-local



OSPFv3

FF02::5 (all OSPF routers), FF02::6 (all OSPF DRs)

Neighbor Authentication done with IPsec (AH)

Address Family Identifier (AFI=2) for IPv6

BGP TCP port 179

Can share IPv6 peers over IPv4 and vice versa, but don't do this. 
Share info for IPv4 over IPv4 BGP session and IPv6 over IPv6 BGP session

THis way we have conguency. 

set link-local IP for vlan FE80::21 for vlan 21, then FE80::1 and FE80::2

Look up flow label for Equal Cost Multipath Routing and Link aggregation

nd cache timers, are they the same?


Gratuitious ARP (RFC 9131)


If A,L,M,O Flags all = 1
	If Windows Server has 4 IPv6 addresses:
		-windows will use stateful address over stateless addresses


L Flag - everyone else on this same prefix is on the linke. dont have to go to the router. 

Clone issues - machine id is the same so the DAD fails and everything gets the same link-local addresss. 

flush neighbor cache


IF we have a datacenter, maybe we need to /48s. just for segregation. 

what inside of building may move outside of the building. 

Think route summarization. 

dont tie the v4 addressing to the v6 addressing. ie. dont put .72 3rd subnet into the IPv6. 

maybe D and U may need two /48s. 


Microsoft's IPAM / Solarwinds IPAM. 

::53 for DNS, ::25 for Mail

FE80::D:3.   

Server A1

Can use different tiers of availability zone.  ::ServerID.  

Code Tier/function and location/number into the last 

function 7th hextet. 8th for the server.

is there a Secuerity benefit to certain numbers? Like 1 for security, 0 for non-security. 

DHCP Scope can be AAAA to FFFF. its 

Some PXE boot software mauy only work with IPv4. 





