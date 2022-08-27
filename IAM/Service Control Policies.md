Feature of AWS Organizations that allows restrictions to be placed on MEMBER accounts in the form of boundaries.

SCPs can be applied to the organizations, to OU's (Organizational units), or to individual accounts. These SCPs inherit down the organizational tree.

Member accounts can be effected, the MANAGEMENT account cannot be affected by SCPs.

SCPs DON'T GIVE permission -- they just control what an account CAN and CANNOT grant via identity policies. They are account permissions boundaries. They limit what the account (including the account root user) can do. It reduces the allowed permissions on the entire account.

Default is a FullAWSAccess policy which essentially means no restrictions. This has the effect of making SCPs a deny list architecture so we need to add each deny explicitly.

To turn it into an allow list, you would want to remove the default FullAWSAccess and explicitly allow to each account. This option can be a lot of admin overhead and is easy to misconfigure and not allow enough.

SCPs determine the boundaries. If they allow something but the identity policy of the account denies it, it won't be granted to the identity.
