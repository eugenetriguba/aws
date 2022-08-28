- Managed Container image registry service
  - Like Docker hub for AWS

- Each AWS account has a public and private registry
- Each registry can have many repositories
- Each repository can contain many images
- Images can have several tags

- Public = public R/O access for anyone. R/W requires permissions.
- Private - permissions required for any R/O or R/W.

- Integrated with IAM - Permissions
- Image Scanning
  - Basic
  - Enhanced (inspector)
    - OS and software packages in containers that works on layers

- Near real-time metrics (to Cloudwatch for auth/push/pull/etc.)

- API Actions => CloudTrail
- Events => EventBridge
- Replication
    - Cross-Region _and_ Cross-Account
