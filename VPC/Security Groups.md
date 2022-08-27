# Security Groups

Another security feature of an AWS VPC. However, unlike NACLs, they are attached to an AWS resource, not VPC subnets.

- Stateful - they detect response traffic automatically.

- Allowed (IN or OUT) request = allowed response automatically.

- No explicit deny, only allow or implicit deny. This means you can't block specific bad actors.

- Allow referencing other AWS logical resources and IP/CIDR and can even reference itself.
  - Self reference allow scaling with add and removes from the SG. Anything that has this particular SG can communicate with anything else that has that particular SG and IP changes are handled automatically. This can be useful to auto provisioned resources or app HA.

- Attached to ENI's, not instances (even if the UI shows it that way).
  - SGs are attached to network interfaces.
  - Applies to allow traffic entering or leaving the ENI.

## Example

Let's say we have a web subnet and an app subnet both in a VPC. We want the web subnet to allow traffic in for tcp/443 for source 0.0.0.0/0 and so we add that for its SG.

However, let's say the web subnet needs to communicate with the app subnet on tcp/1337. We _could_ use just the single IP of the single and allow that in the app subnet or use the whole range of the subnet. However, with SGs, we can actually just reference the web's SG and allow that. This will end up allowing anything that has that SGs attached to them.

Referencing the SGs allows to scale really easily. This is because any new instances inside of the web SG are automatically allowed to communicate with the app SG.

