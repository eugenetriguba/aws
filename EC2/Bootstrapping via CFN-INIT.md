# Bootstrapping via CFN-INIT

- cfn-init helper script (installed on EC2 OS)

- Simple configuration management system

- Procedural (User Data) vs Desired State (cfn-init)

- Packages, groups, users, sources, files, commands and services.

- Provided with directives via Metadata and AWS::CloudFormation::Init on a CFN resource.

- While user data runs once, cfn init can be configured to watch for updates on the metadata on an object in a template and if it changes, then cfn init can be executed again and update the configuration of that instance to the desired state specified in the template.

## CreationPolicy and Signals

- CFN has created the resource and passed in the user data, but CFN doesn't understand the user data. If the user data has a problem and the bootstrapping process fails, CFN won't know. The instance will be marked as complete regardless.

- A Creation policy is something that is added to a logical resource inside CFN template. You create it and supply a timeout value. It is used to create a stack and create an instance. However, it doesn't move it to a create complete state until it gets a signal from the resource itself that it has successfully completed. Therefore, even though EC2 has launched the instance, CFN waits for a signal from the resource itself to know that it is good to go (`cfn-signal`).
