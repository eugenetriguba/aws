A type of policy that gets attached to identities inside of AWS.

Identities: IAM users, IAM groups, and IAM roles.

Architecture and how policies work

* A set of security statements to AWS. Grants or denies access to an AWS product or feature to an identity that uses that policy.
* Identity policies, also known as policy documents, are created using JSON or YAML.
* When an identity attempts to access AWS resources, that identity needs to prove who it is to AWS (authentication). Once authenticated, it is known as an authenticated identity and knows which policies an identity has (which can have multiple statements). It also knows which resource or resources you want to interact with as well as the actions you're performing on them. 

Example

````yaml
Version: 2021-10-17
Statement:
	- Sid: FullAccess
	  Effect: Allow
	  Action: ["s3:*"]
	  Resource: ["*"]
	- Sid: DenyCatBucket
	  Effect: Deny
	  Action: ["s3:*"]
	  Resource: ["arn:aws:s3:catgifs", "arn:aws:s3:::catgifs/*"]
````

Sid = Statement ID (What does this statement do? Best practice to always use this (why?))
Effect = (allow/deny)
Action = service:action
Resource = 

For specific resources, you want to use the arn. Wildcards are allowed for actions/resources. It is possible to get and be denied access for a resource.

Every interaction you have with AWS is a combination of the resource and action you're attempting to do on the resource. The statement only applies if it matches the action and the resource.

Rules

1. Explicit DENYs
1. Explicit ALLOWs
1. Default DENY (implicit)

AWS accounts start off with no access to any AWS resources. If they are not allowed access, they have no access.

When determining permissions, AWS will aggregate all user policies, group policies, and specific resource policies for the action being attempted.

Types:

* Inline
  * Assign full policy individually to each account.
  * Useful for special circumstances or exceptions.
* Managed
  * You create a managed policy and attach that policy to each account. Impacts all identities when changed.
  * Reusable, low management overhead. Used for the normal default operation rights.
  * AWS managed policies
  * Custom managed policies
