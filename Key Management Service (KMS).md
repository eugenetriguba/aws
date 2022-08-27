* Regional and public service
* Every region is isolated when using KMS (can be thought of as a separate product in each region).
* Allows creating, storing, and managing keys
* Symmetric and Asymmetric keys
* Cryptographic operations (encrypt, decrypt, ...)
* **Keys never leave KMS** - Provides FIPS 140-2 (L2) (https://csrc.nist.gov/publications/detail/fips/140/2/final)

## Customer Master Keys (CMK)

* CMK - Customer Master Key
* I, other applications, and other AWS services can use them.
* Logical, container for the actual physical master key.
  * Contains ID, date, policy, description, and a state of the key (active or not).
  * Backed by physical key material
* Generated or imported in
* CMKs can be used for up to **4KB of data**
* Never stored in a persistent form when not encrypted.
* Encrypted before it is stored on disk

Encrypt operation can be performed by supplying data and the CMK key to use and assuming the identity has the permissions to use that key. To decrypt, the identity does not need to specify the key since it is encoded in the ciphertext of that data to decrypt.

Different people and different roles are given access rights within the product.

## Data Encryption Keys (DEKs)

* GenerateDataKey via CMKs - works on > 4KB

* Linked to the CMK

* **KMS does not store the DEKs in any way**
  
  * Provides it to you or the service using KMS and then discards it
  * KMS does not perform the encryption or decryption of data using DEKs. You or the service does that.
* Provided plaintext version of the key and ciphertext version using the CMK.

* Flow
  
  * Generate data encryption key
  * Receive plaintext and ciphertext version of key
  * Encrypt the data using the plaintext key
  * Discard plaintext key
  * Generally then store the encrypted key with the encrypted data
* KMS does not perform the encryption/decryption on data larger than 4KB using the DEKs. You or the service does.

* KMS does not track the usage of DEKs. Can be used to encrypt hundreds or millions or files or can request new one for each one of the files.

* By storing the encrypted key with the data, you always have the right key for the data to use.

* Pass the encrypted key to KMS and ask to decrypt using the CMK that was used to generate it. Then use the plaintext DEK to decrypt the data and discard plaintext DEK.

## Key Concepts

* CMKs are isolated to a region & never leave
* AWS Managed or Customer Managed CMKs
* Customer managed keys are much more configurable
* CMKs support key rotation
* Backing key (and previous backing keys caused by rotating)
* Aliases to particular CMKs (also per region)

## Key Policies and Security

* Key policies (resource)
* Every CMK has a key policy.
* Customer managed keys can adjust the policy.
* Keys need to be told that they trust the AWS account that they are in.
* IAM needs to trust account and account needs to be trusted by the key.
* Difference between identities that can manage a key and identities that can use the key to encrypt/decrypt
