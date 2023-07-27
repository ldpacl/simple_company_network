A SIMPLE COMPANY NETWORK USING CISCO PACKET TRACER


This is a simple network design and implementation project for beginners.

Problem statement:

Design a network in CISCO packet tracer to connect ACCOUNTS and DELIVERY departments through the following:
a. Each department should contain at least 2 PCs.
b. Appropriate number of switches and routers should be used in the network.
c. Using the given network address 192.168.40.0, all interfaces should be configured with appropriate IP addresses, subnet mask and gateways.
d. All devices in the network should be connected using appropriate cables.
e. Test the connectivity between ACCOUNTS and DELIVERY department PCs.

Solution:

Given:
network: 192.168.40.0/24
subnet mask: 255.255.255.0

Number of subnets = 2 (because there are two departments)

Therefore 2^n = 2 ==> n=1

1 bit is borrowed from the host portion for subnetting

New subnet mask = 255.255.255.128


ACCOUNTS
.Subnet mask: 255.255.255.128
.Network ID: 192.168.40.0
.Address range: 192.168.40.1 to 192.168.40.126
.Broadcast Address: 192.168.40.127

DELIVERY
.Subnet mask: 255.255.255.128
.Network ID: 192.168.40.128
.Address range: 192.168.40.129 to 192.168.40.254
.Broadcast Address: 192.168.40.255

Configure the router and end devices using the above subnet.
