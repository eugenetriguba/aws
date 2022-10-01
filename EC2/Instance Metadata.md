# Instance Metadata

EC2 Service that provides data to instances. It is data about the instance that can be used to manage or configure a running instance. This provides a way for the instance to access information about the environment that it wouldn't be able to access otherwise.

It is accessible inside ALL instances at http://169.254.169.254/latest/meta-data

## Information provided

- Environment
	- For instance, host name, events, security groups, etc.

- Networking
	- While OS can't see IPv4 public addressing, the instnace metadata can be used to get access to that information.

	- Authentication
		- Instances themselves can be given permission to access resources and the metadata is how application on the instance can gain access to temporary credentials geberated by assuming the role.
	- Temporary SSH keys. Instance connect will pass in an SSH key behind the scenes that is used to connect.

- User-Data

- The metadata is **not authenticated or encrypted**. If you're able to get access to the EC2 instance, you can access it. However, you can restrict it with per-instance firewall settings that restrict access to that IP address but that is extra per-instance admin overhead. In general, the metadata should be treated as something that can and will be exposed.

