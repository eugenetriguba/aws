IAM Groups are containers for users.

* Solely for organization of large set of users.
* Groups have no credentials and you can not log into them.
* User can be part of multiple groups.
* Groups can have inline and managed policies.
* No effective limit for number of users in group.
* There is no group with all users. However, you could create it yourself.
* You cannot have groups within groups.
* Soft limit of 300 groups per account (can be increased via support ticket).
* While users and roles can be referenced via an ARN, groups are not a true identity and cannot be referenced as a principal in a policy.
* A resource policy cannot grant access to an IAM group. You could to users.
