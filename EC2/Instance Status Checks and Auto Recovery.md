# Instance Status Checks & Auto Recovery

Every instance in EC2 has 2 high level per instance status checks.

- System status
	- Failure of this means one of a few major problems:
		- Loss of system power
		- Loss of network connectivity
		- Host software issues
		- Host hardware issues

- Instance Status
	- Failure of this may mean:
		- Corrupted file system
		- Incorrect instance networking (for instance, setting a public IPv4 address in the OS)
		- OS Kernel issues

These issues can be recovered from manually or you can have EC2 attempt automatically stop a failed instance, reboot it, terminate it, or perform auto recovery.

Auto recovery moves the instance to a new host, starts it up with exactly the same configuration as before and if software on the instance is setup to auto start, this could mean that the instance recovers fully and automatically from any failed checks.

EC2 is AZ resilient so this automatic recovery won't protect against an entire AZ failure, only an isolated failure with the host or instances. Furthermore, it depends on available EC2 host capacity. In the case of a major failure in the AZ in a region, there is a chance this won't work if there is no capacity. Also, you also need to be using modern types of instances. Lastly, this won't work with instances that use instance store volumes (so only instances with EBS volumes attached).

This feature isn't designed to handle large scale failure or complex issues that are occurring. However, it does allow handling simpler system issues automatically.

Further reading: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-recover.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-recover.html)
