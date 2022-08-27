Identity for a single individual or "thing" which will use that identity. Used for anything requiring long-term AWS access e.g. Humans, applications, or service accounts.

Principal -> Request --> IAM

* Username and password
* Access Keys

Once authenticated, it is now an authenticated identity.
Then any actions it tries to do, it then attempts to authorize that it is allowed to do so.

Amazon Resource Names: Uniquely identify resources within any AWS accounts.

* arn:partition:service:region:account-id:resource-id
* arn:partition:service:region:account-id:resource-type/resource-id
* arn:partition:service:region:account-id:resource-type:resource-id

Example: 

* arn:aws:s3:::catgifs      -- Bucket
* arn:aws:s3:::catgifs/\*  -- Objects in the bucket (no overlap between the two)

Exam Powerup

* **5,000** IAM Users per account
* IAM User can be a member of 10 groups
* This has systems design impacts..
* Large orgs & org merges
* Internet-scale applications
* IAM Roles & Identity Federation fix this (more later)
