# Network Address Translation

## Purpose

NAT is designed to overcome IPv4 shortages. Furthermore, it also provides some security benefits.

A NAT translates private IPv4 addresses to public IPv4 addresses and then translates back in reverse so Internet-based hosts can communicate back with the private services (each type of NAT handles this process differently).

A NAT only makes sense within the context of IPv4 because the smaller amount of IP addresses. It makes no sense with IPv6 where we don't have this problem.

## Types

### Static

Translates from 1 specific private address to one specific (fixed) public address. This is how IGW works.

The router (NAT device) maintains a NAT table where it maps private IP <-> public IP (1:1).

### Dynamic

Translates from 1 private address to 1st available public address from a pool.

This method is generally used when you have a large number of private IP addresses and want them all to have internet access via public IP but when you have less public IP addresses than private IP addresses and want to be efficient in how they're used.

Only one private IP will be mapped to any given public IP at any time. It is still 1:1 for the duration of the allocation.

Furthermore, if the public IP pool is exhausted, external access can fail.

### Port Address Translation (PAT)

Many private addresses are translated to a single public address (NATGW). This is likely what your home internet router does.

MANY:1 mapping (private ip to public ip) architecture.

Source IP address is constant whereas source port is unique per device. This is the case even if the private source port is the same as another device. Therefore, when the device at the destination IP wants to communicate back, it will send it to the NAT public IP and a port of a public port for whichever device initiated the connection.

