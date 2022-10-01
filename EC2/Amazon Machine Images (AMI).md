# Amazon Machine Image

Template of an instance configuration and use that template to create many instances from that configuration. AMIs are used when you launch EC2 instances, but those are usually AWS-provided AMIs. There are also community and marketplace (for commercial software) provided AMIs.

- Regional (unique ID e.g. ami-0a887e401f76...)
- Controls permissions (Public, your account, or specific accounts)
  - By default, your account.
- You can create an AMI from an EC2 instance you want to template.
- It does not on its own contain any real data volume. It is a container that references snapshots that are created from the original EBS volumes with the original device IDs. With that, you can take that AMI to provision instances with exactly the same data and exactly the same configuration of volumes.

## Lifecycle

1. Launch
  - Use an AMI to launch an EC2 instance.
  - EBS storage presented as block IDs (boot = /dev/xvda and data = /dev/xvdf usually)

2. Configure
  - Apply some custom configuration to get it to a state where it is configured setup.
    - Might be an OS with certain apps or services installed, might be volumes attached, or might be a full application suite installed.

3. Create Image
  - Based on that configured instance, you can use that to create an AMI.
  - EBS snapshot is created for that instance.
  - Logical container that hold associated information.
    - AMI ID
    - Permissions restricting who can use it.
    - Snapshots are referenced in the AMI using a block device mapping.
	- Table of data. Links snapshot IDs to device ID that the orignal volumes had on the EC2 instance.
	- When this AMI is used to create a new instance, this instance will have the same EBS volume configuration as the original.
    - Snapshots are used to create new EBS volumes in the AZ that you're launching the instance into and those volumes are attached to that new instance using the same device IDs that are contained in that block device mapping. They are a regional construct.

4. Launch (again)

## Exam Powerups

- AMI = **One Region**. They only work in that region. But they can be used to be deployed in the other AZs in that region.
  - AMI baking: taking an EC2 instance, installing all the software, doing all the config changes, and baking all of that into an AMI.
- An AMI _cannot_ be edited. Launch an instance, update the configuration, and make a new AMI.
- Can be copied between regions (includes its snapshots).
- Remember permissions. Default = your account.

