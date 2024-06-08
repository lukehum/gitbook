
Student37

Student Guides uploaded to GOogle drive -> IPv6

Ctrl-Alt-SHift   < copy paste into guacamole

ip addr show

ifconfig ens33

ping6 2001:db8:12::1

ping6 2001:db8:11::6

ping6 chapeau.hoggnet.com

ping6 2001:db8:22::7

ping6 derby.hoggnet.com



==Add Reverse Lookup Scope first within Microsoft DNS==

Microsoft Legacy IPv6 DNS Servers

They use fec0:0:0:fff::1/2/3 - uses site-local deprecated addresses as DNS Servers (RFC3879) if it can't get DHCPv6 and DNSv6.

DNS Manager application -> Properties
Only the following IP addresses
select the correct IP address of the DNS servers.

DHCPv6 cannot exist without Router RA

DHCPv6 
	- RFC 3315
	- RFC 8415

DHCPV6 
	- A flag off
	- M flag on

SARR
	- Solicit
	- Advertise
	- Requeest
	- Reply

DHCPv6 Client DUID
- may use a different MAC of a diff interface to generate its DUID. Windows. 

no ipv6 nd autoconfig prefix

dhclient 
	- force 

DHCP OPtion 108 
	- disable IPv4 on network with DHCP (windows clientd do not have enabled)

RDNSS
	- can push DNS server for Android devicees that dont do DHCPv6
	- ipv6 nd ra dns server blablah



ipv6 nd ra suppress
ipv6 address 2001:db8:1000:1230::1/64


==Turn O Flag off==

NCSI workaround in BIND


IPv6 address of www.sprint.next 

tracert 2600::





