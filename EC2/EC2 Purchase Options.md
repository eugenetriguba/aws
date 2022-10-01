# EC2 Purchase Options

## On-Demand

- Most unremarkable. No specific pros or cons.
- On-Demand instances are isolated but multiple customer instances run on shared hardware.
- Instances of different sizes run on the same EC2 hosts - consuming a defined allocation of resources.
- Per-second billing while an instance is running. Associated resources such as storage consume capacity, so bill, regardless of instance state.

### When to use?

- Default purchase option
- No interruption
- No capacity reservation
- Predictable pricing
- No upfront cost
- No discount
- Short term workloads
- Unknown workloads
- Apps which can't be interrupted

## Spot

- Cheapest way to get access to EC2 capacity.
- Spot pricing is AWS selling unused EC2 host capacity for up to a 90% discount. The spot price is based on the spare capacity at a given time.
- If the spot price goes above the maximum price you set, then any spot instances which you have are terminated.
- Spot instances should not be viewed as reliable.

### When to use?

- Never use spot for workloads which can't tolerate interruptions.
- Not time critical
- Anything which can be rerun
- Bursty capacity needs
- Cost sensitive workloads
- Anything which is stateless

## Reserved

- NO reservation = Full per/s price.
- Matching instance, reduced or no p/s price.
- Unused reservations are still billed.

- Reservations can be locked to AZ or region.
- Partial coverage of larger instance.
- A commitment to AWS that you will use resources for a length of time. In return for that commitment, you get those resources cheaper. Once you have committed, you pay, whether you use them or not.
- A commitment is for 1 year or for 3 years. The cost is less for 3 years but so is the risk.

### Payment structures

- No-Upfront: Agree to one or three year term for a lower per/s fee. Least discount of the three for this option.
- Partial upfront: Smaller lump sum in advance for a lower per/s fee (lower than no upfront).
- All upfront: No per/sec fee for the instance (offers the greatest discount).

## Scheduled Reserved Instances

- Scheduled reserved is ideal for long-term usage which doesn't run constantly.
- i.e. batch processing daily for 5 hours starting at 23:00
- Doesn't support all instance types or regions. 1,200 hours per year and 1 year term minimums.

## 

## Dedicated Host

- Pay for the host
- Any instances that run on the host have no per/s charge.
- Might have software that is licensing based on sockets or cores in a physical machine.
- Host affinity links instances to hosts.

# Purchase Options Summary

## Default/Shared

- No Host exposure
- Per second charges
- No capacity management required

## Dedicated Hosts

- Pay for the host.
- No instance charges.
- Capacity management required.

## Dedicated Instances

- You don't own or share the host.
- Extra charges for instances but dedicated hardware.
- AWS commits to not using any other instances from any other customers on that hardware.
- One off hourly fee for any regions where you are using dedicated instances (regardless of how many you are using).
- Fee for dedicated instances themselves
- Common for sectors of the industry that have really strict requirements where you can't share hardware.

