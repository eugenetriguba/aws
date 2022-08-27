# Network Access Control Lists (NACLs)

A network access control list (ACL) is an optional layer of security for a VPC that acts as a firewall for controlling traffic in and out of one or more subnets.

These affect connections going into a subnet and out of a subnet but **not** for connections between infrastructure _within_ the subnet.

Inbound rules only affect data entering the subnet and outbound rules only affect data leaving the subnet. Importantly, these rules are focused on the direction of traffic and _not_ on whether it is a request or response. This is a firewall that is **stateless**.

Rules match the destination IP/range, port, and protocol and ALLOW or DENY based on that match.

Network ACLs allow both explicit allows and explicit denys.

Rules are processed in order. First a network ACL determines if the inbound or outbound rules apply. Then, it starts from the lowest rule number. It evaluate traffic until each rule until it finds a match. Lastly, it is allowed or denied based on that rule and processing stops.

Therefore, even though you might have both explicit allow and deny rules, if the deny rule comes first, the allow rule might never be processed. It is also worth mentioning that rule numbers are unique for inbound and outbound rules.

As a catch all, an asterick is used and is used as an implicit deny for anything not caught with the rules.

Because ACLs are stateless, rules are required for both the request and response portion of a connection. So for a web server, we might have a rule that allows connections using TCP to port 443. While that covers the request, we would need an outbound rule for the response as well for TCP on an ephemeral port range (1024-65535). While this isn't incredibly secure, it is the only way with stateless firewalls.

Now what if we have two servers in two different subnets that need to communicate? Then we would need four rules. Then if those servers also need software updates, we'll need more rules there. So we can see how this can get more complex fairly quickly.

These rule pairs (app port & ephemeral ports) are needed on each NACL for each communication type which occurs 1) within a VPC 2) TO a VPC or 3) FROM a VPC.

When a VPC is created, it uses a default NACL that has an implicit deny (*) and an ALLOW ALL rule. The result is that all traffic is allowed and the NACL has no effect. This is designed to be beginner friendly and reduce admin overhead since AWS prefers using security groups.

Custom NACLs can be created for a specific VPC and are initally associated with NO subnets. They start with only 1 inbound rule (the implicit deny) and 1 outbound rule (the implicit deny) and the end result is that _all traffic is denied_.


Key points

 - Stateless so request and response are seen as different which ends up requiring to create two rules, 1 inbound and 1 outbound.

 - Only impacts data crossing subnet boundary.

 - NACLs can explicitly allow and deny. They're a great security feature when you need to block any traffic attempting to exploit your system.

 - Allow using IPs/CIDR, ports, and protocols. They don't have awareness of logical resources.

 - NACLs cannot be assigned to AWS resources - only subnets.

 - Use together with Security groups to add explicit DENY (Bad IPs/Nets)

 - Each subnet can have one NACL (default or custom)

 - A NACL can be associated with MANY subnets.
