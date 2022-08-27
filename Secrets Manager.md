* Shares functionality with Parameter store
* Designed specifically for secrets (API keys, passwords, etc.)
* Usable via Console, CLI, API, or SDKs
* Supports automatic rotation of secrest (using lambdas)
* Directly integrates with some AWS products (RDS, etc.)
* Secrets are encrypted using KMS

## What sets secrets manager apart from Parameter store?

* Periodically, we can invoke a lambda to rotate the secrets (and products such as RDS are kept in sync)
