# IP-Range
IP Range network by the mask and CIDR notation mapsler

Like you say there is a few ways to 192.168.0.x

192.168.0.0-192.168.0.255
while this may seem like the simplest way of describing your network, there is no way to distinguish if you're describing an IP range within a larger range (192.168.x.x for example) or the network itself.

192.168.0.0/255.255.255.0
192.168.0.0/24
Described the network by the mask and CIDR notation.
Both are essentially describing the same thing, but CIDR easier to distinguish once you've worked with it for a while.
To understand the number (24) in CIDR you need to go binary, lets take 192.168.0.0

bit 1-8	bit 9-16	bit 17-24	bit 25-32
ip	192	168	0	0
ip	1100 0000	1010 1000	0000 0000	0000 0000
/16	255	255	0	0
/16	1111 1111	1111 1111	0000 0000	0000 0000
/24	255	255	255	0
/24	1111 1111	1111 1111	1111 1111	0000 0000
/29	255	255	255	248
/29	1111 1111	1111 1111	1111 1111	1111 1000
netmask in italics				
The netmask describes what parts of the IP address is on your local network, basicly anything with a corresponding 1 in the netmask (see above) is not on the local network and needs to be routed (usually by your default gateway).

Now explaining the /24, you set netmask bits 1-24 to 1, which gives you the last 8 bits (192.168.0.0-255) as local addresses. If you had a /16 you would set bits 1-16, giving you 16 bits (192.168.0.0-192.168.255.255) as local addresses.

