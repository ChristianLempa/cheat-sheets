# cidr - Classless Inter-Domain Routing

Before CIDR and Variable Length Subnet Masks, IP addresses had fixed subnet masks

Class C had a 24 bit prefix (/24), Class B had a 16 bit prefix (/16), and Class A had an 8 bit prefix (/8)

**[Note:]** The prefix determines how many addresses are covered by the CIDR address. The prefix is the number of bits reserved for the network portion of the address

An IP address consists of a host and a network portion

The 32 bit string below represents a /16 network since 16 bits are dedicated to the network portion of the address

## Network bits / Host bits

`11111111 11111111 / 00000000 00000000`

As an example, if we were to make a subnet with only 2 addresses on the 3.3.3.0 network, the network prefix would be /31

If we view this in binary it would look like:

`00000011.00000011.00000011.00000000 (3.3.3.0)`

The subnet mask then becomes:

`11111111.11111111.11111111.11111110 (/31)`

In the subnet mask above, only one bit is available for modification, so the only two available IP addresses would be: 

`3.3.3.0 and 3.3.3.1`

`3.3.3.2` would represent the start of another subnet 
 
If we changed the prefix to /30, the new IP address range would be:

`3.3.3.0 - 3.3.3.3`

