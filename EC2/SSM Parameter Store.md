# SSM Parameter Store

A service in Systems Manager which allows the storage and retrieval of parameters (strings, string lists, secure strings).

The service supports encryption which integrates with KMS, versioning and can be secured using IAM.

The service integrates natively with many AWS services and can be accessed using the CLI/APIs from anywhere with access to the AWS Public Spare Endpoints.

- Storage for configuration and secrets

- Supports String, StringList, and SecureString

- can be used for license codes, database strings, full configs and passwords

- Hierarchies and versioning

- Plaintext or ciphertext (integrates with KMS)

- Public parameters (Latest AMIs per region)
