Root User \<=> Account

* The root user can in many ways be thought of as the accounts since we cannot remove or ever restrict the root user without deleting the entire account.

IAM: Identity and Access Management

* Every AWS Account comes with its own copy of IAM, it's own database.
* Globally resilient service. Any data is always secure across all AWS regions (?)
* Identities start with no permissions and can be granted (almost) up to those held by the root user.
* The IAM service is trusted fully by your AWS account. (Has all permissions the account and account root user has).

IAM Objects

* Users
  * Identities which represent humans or applications that need access to your account.
  * Can have at most 1 username and 1 password (password is optional, can use access key only).
* Groups
  * Collections of related users (development team, finance, etc.)
* Roles
  * Can be used by AWS Services (i.e. all ec2 instances to access S3, numbers are uncertain, users are for individual instances) or for granting external access to your account.

Policy: Allow or Deny access to AWS services, only when attached to users, groups, or roles. (On their own, they do nothing).

IAM Responsibilities:

* Manages Identities - An Identity Provider (IDP)
* Authenticates (Prove you are who you claim to be)
* Authorize (Allows or denies access to resources)

Basics

* No cost (however, there are limits)
* Global service / Global resilience (can cope with large failures in the AWS infrastructure)
* Allows or denies its identities on its AWS account
* No direct control on external accounts or users (local)
* Allows Identity federation (such as allows use of Microsoft Active Directory) and MFA

IAM Access Keys

* Each IAM User can have 0-2 access keys
* They can be created, deleted, made inactive, and made active.
* Made up of an Access Key ID and Secret Access Key
* IAM Roles don't use access keys
