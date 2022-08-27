Product that allows larger businesses to manage multiple AWS accounts in a cost effective way with little to no overhead.

A organization is created with an account that then becomes the management account for that organization. 

Accounts can then join that organization and become member accounts.

Hierarchical organization

* Organizational root container (not to be confused with root user of an account, which gives full access over a particular account)
* Root organization root is just a container for other organizations (top of the tree).
* Organizations allow consolidated billing. Payer/Master/Management account contains the payment method for all the other accounts.
* Consolidation of reservations and volume discounts.
* Organizations don't need to have IAM users within every account. Roles can be used to access other AWS accounts.
* 
