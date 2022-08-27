AWS Regions

* Doesn’t directly map onto a continent or a country
* Creation of AWS. Area of the world that they have selected and inside of it, there is a full deployment of AWS infrastructure.

AWS Edge Locations: 

* Much smaller than regions (but located in many more areas)
* Tend to only have content distribution services as well as some types of edge computing
* Ideal for companies like Netflix that need to store their TVs and movies as close to their customers as possible (low latency, higher speed).

Some services act from a global perspective (but few), however, most are region specific deployments.

Benefits of AWS Regions

* Geographic Separation leads to isolated fault domain (designed to be 100% isolated)
* Geopolitical Separation - Different governance
* Location Control - Performance

To refer to a region, you can use:

* Region code (ap-southeast-2)
* Region name (Asia Pacific (Sydney))

Inside every region, there are multiple availability zones provided. With these zones, you have isolated infrastructure within each region. If there is an issue in one availability zone, you’ll still have infrastructure running in the other zones within the region. It’s a way to provide more fault tolerance and resilience. 

An availability zone is not a data center. It could be multiple. AWS doesn’t give you visibility into this. Just that they are isolated and connected with high speed, low latency, redundant networking.

Resilience

* Globally resilient service (data is replicated across multiple regions across AWS, no concept of picking a region). IAM and Route 53 as examples.
* Region Resilient services operate in a single region with one set of data per region. You could create a RDS database in Sydney and one in northern Virginia. They are different and generally replicate data to multiple availability zones.
* AZ Resilient services are services that are run from a single availability zone. If that zone fails, that service will fail. Prone to failure.
