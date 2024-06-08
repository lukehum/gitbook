
DoD Instruction 8440.XX / DoD CIO
DoD Directive 5144.02
OMB M-21-07 / DoD Directive-type Memoranedum -  21-004 - Department of Defense Implementation of Internet Protocol Version 6

DoD IPv6 Implementation Plan Fiscal Years (FY) 2021-2025, 30 September 2021 - 20%, 50%, and 80% of IP enabled assets operating in IPv6 environments by the end of 2023, 2024, and 2025, 

Identify and justify DoD info systemes that cannot be converted and provide a schedule for replacing or retiring these sytems. 

DoD and its Components will transition its info systems networks from IPv4 only to eventually an IPv6 only enterprise in accordince wwith DoD IPv6 Implementation Plan



Scott Hogg - Instructor - Hexabuild


- IPv6 buzz podcast  
- networkworld website


0800 EST - 1200 EST (break .5 hr) 1230 EST - 1630

- RFC 8200 


20 bit Flow Label field

IPv6 Routers don't fragment packets (e.g. requires PMTUD)

Link-Local addresses, dynamic node identifier addressing
	- Only LAN based communications
	- L-Flag set

IPv6 extension headers. 

SCTP? DCCP? transport layer

MLD? layer 3

TOS -> traffic Class = QOS migrates over and is same.



FE80::/10
fe80/febf link local

==1111 1110 10==00 0000 (F E 8 0)
==1111 1110 10==01 0000 (F E 9 0)
==1111 1110 10==10 0000 (F E A 0)
==1111 1110 10==11 0000 (F E B 0)
.
.
.
==1111 1110 10==11 FFFF (F E B F)



==1111 1110 10==11 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 

similiar to 
192.168.0.0/23
is 
192.168.0.0
==1100 0000  . 10101000 . 0000000==0 . 00000000
to
==1100 0000  . 10101000 . 0000000==1 . 11111111
192.168.1.255

==11111111.11111111.1111111==0.00000000  /23



FEBF

1111 1111  1100 0000  (/10)
CANNOT change 1s, Can change 0s. 


``ping FE80::0%12

link local address
blablah%12
%12 is the interfce number. zone identifier

Global
Unique Local
LInk Local

Insert IPv4 address inside an IPv6 address.
IPv4 mapped IPv6 addresses (::ffff:/96)

0000:0000:0000:0000:0000:FFFF:129.168.12.34 (convert to hex)

Unique Local Addresses
FC00::/8 and FD00::/8

FD(40bit random number -  global ID):abcd:abcd:abcd:abcd
- Global ID is pseudo random to avoid conclicts
- ULAs
- DONT USE

C:\Users\User>netsh
netsh>int ipv6
netsh interface ipv6>show prefixpolicies
Querying active state...

Precedence  Label  Prefix
----------  -----  --------------------------------
        50      0  ::1/128
        40      1  ::/0
        35      4  ::ffff:0:0/96
        30      2  2002::/16
         5      5  2001::/32
         3     13  fc00::/7
         1     11  fec0::/10
         1     12  3ffe::/16
         1      3  ::/96

netsh interface ipv6>



RA Message data

A Flag - address autoconfiguration
L Flag - On-Link Flag
MTU size for link (optino 5)
O Flag - 

Router Lifetime (1800)


A Flag
 - Do I allow stateless address assignments?
 L Flag ????



SLAAC

unicast
multicast
CEF on


Default interface cisco
- Dual-Protocol, RA A=1, L=1, M=0, O=0


`ipv6 route ::/0 2001:db8:1:1


`show ipv6 int vlan 11

`show ipv6 neighbors

`ipv6 nd managed-config flag`
`ipv6 nd other-config-flag`

##See if this is on NXOS##
`ipv6 nd prefix default no-autoconfig`

`show route


==reference slides==



temporary IPv6 addresses

- uses thi swhen it makes connections off network
- 


##IPv6 test page ##

`derby.hoggnet.com`

LInux multiple IPs
secured/temporary/clat46


For changing static routes on diff linux distros
/etc/dhcp.conf file
/etc/networkmanger/'wired connection 1.nmconnection'

Linux
ip -6 neighbor show

Eveery node is listening for multicast addresses

Shows solicited multicast groups on windows
`netstat -g6

Neigh solicitation 135 and advertisement 136

RFC 6555 - Happy eyeballs - chosing between IPv4 and IPv6

http\:\/\/[2001:db8:22::7]

http\:\/\/[2001:db8:22::7]:8081

Translation
	- NAT64/DNS64 (RFC 6146/6147)
	- SMTP embeds IPv4 in its payload. this would not get translated

Can use Load balancers to terminate IPv6 connections and then translate to IPv4 to talk to old IPv4 only system.

Stateless IP/ICMP Translation (SIIT)
	- RFC 7915 - 
	- RFC 7755 - datacenter environments
	- Uses ::ffff:0000:==0000:0000==/96 (highlighted is the IPv4 address translated to IPv6)

DNS64 / NAT64

DNS Tricks that IPv4 node is available over IPv6

IPv6 node does DNS query, DNS64 server sees if dest has v4 or v6, 
	if dst node is ipv6
		- reeplys
	if dst node is ipv6 and ipv4
		- replys
	if dst node is ipv4 only
		- replys DNS AAAA record response, sens Well known prefix 64:ff9b:: (RFC 8781) 
		go to NAT64 ttranslator
			- It seees you are connecting to 64::ff9b:: and it translates it over to IPv4 address destination. 		


Query from IPv6 only host to get a NAT64 WKP
`dig @2001:db8:11::6 twitter.com AAAA`

`ping6 nginx4.hoggnet.com`



NAT64 only for IPv6 only, otherwise, just use regular DNS for the redirect. 



DNS64/NAT64 is for V6 only nodes


464XLAT - combination of Stateful and Stateless Translation
RFC6877
- Customer tranlsator on phone
- Provider translator on service providers network
- Translated connection - 


CLAT
	- IPv4 only App and IPv4/IPv6 App can communicate over CLAT
	- shows CLAT46 in interface information ifconfig

Experiences from an IPv6-Only Network
	- RFC 6586


https://wwww.youtube.com/watch?v=x4HL4ZMsLE


Cloud Guru - AWS IPv6 class




Unique IPv6 Prefix per Host RFC 8273

DEFCON talk IPv6 scanning

IPv6 Fundamentals, Rick Graziani


IPv6Buzz
Infoblox
Network world


https://download.demisto.com/download-params?token=YOUR_TOKEN&email=YOUR_REGISTERED_EMAIL&eula=accept&downloadName=signed

That is the signed URL, just fill in your token and registered email address

https://download.demisto.com/download-params?token=YOUR_TOKEN&email=YOUR_REGISTERED_EMAIL&eula=accept&downloadName=signed_public_key

That is the key file, same thing as above