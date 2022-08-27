Type of identity that exists inside of an AWS account.

Role may be used be an unknown number or multiple principles (i.e. users, apps, etc.).

* Generally used on a temporary basis
* Something assumes that role and then becomes that role
* A role represents a level of access inside of AWS

What is the difference between logging into a user and assuming a role?

* Both cases, you get the access rights of that identity.

IAM Roles

* Trust policy
  * Which identities can assume the role
  * Can reference identities in the same account (or services) or reference identities in other accounts (or even anonymous usage of that account).
  * Generates temporary security credentials for that role (time limited)
* Permission policy
  * Which permissions that role has
* Can be references within resources via ARNs
* `sts:AssumeRole` (secure token service)

When to use IAM Roles

* AWS Lambda (give lambda some code and create a lambda function)
  * No permissions by default and not an identity
  * Needs some way of getting permissions to do things when it runs
  * Can create a lambda execution role with a trust policy with that lambda service for allowing that lambda to assume that role when it is executing and has those permissions that it needs. It can then `sts:AssumeRole` and retrieve credentials to do the actions it needs to do.
  * Number of running lambdas would be unknown (could be 0, 50, etc.)
  * If no role, then you would need to hard code permissions. You want to avoid that for two reasons
    * Security risk
    * Causes problems if you ever need to change or rotate access keys
* Emergency or out of usual situations
  * Customer support center with usual read-only access but having an emergency role that can be assumed (and is logged) for exceptional situations
* SSO or > 5000 identities
  * Roles are often used when you want to reuse your existing identities within AWS
  * External accounts can't be used in AWS directly to access AWS resource (such as an AD account)
  * Existing role -> Role for temp period -> AWS resource
    * ID federation
* Ride sharing app for millions of users
  * Web Identity federation
  * FB/Twitter/etc. account used to sign in to app and assumes IAM role to access AWS resource
  * No AWS credentials on the app
  * Uses existing customer logins
  * Scales to > 5000 of accounts

Cross-account access

* Identities in your account assume role in partner account in order to access AWS resource in that account
