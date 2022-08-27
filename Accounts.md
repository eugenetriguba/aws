Accounts are containers for Identities (users) and resources.

* Each account has a name (i.e. prod), unique email address, and a credit card (the account payment method as resources are used).
* Every AWS account has an account root user.
* The root user is specific to each account and has full control over the account, and resources created in it, and cannot be restricted.
* AWS is a pay as you consume platform

Identity and access management (IAM) is what is used to restrict access to resources. Users, Groups, and Roles can also be created and given full or limited permissions. These are specific to account but there are cross account permissions (containers).

* Any IAM user starts with no permissions and must be explicitly given them.
* These accounts are great for containing any errors and bad accounts and not having them to spill over to other accounts. For this reason, it’s useful to have separate accounts for development, test, staging, production, etc.
* By default, all access is denied for other accounts and resources except for the root user. However, external identities can be granted access if desired.
