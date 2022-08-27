* Default is no encryption
* Provides encryption at rest for volumes and snapshots
* Decrypted copy of DEK is only ever store din memory of the EC2 host while it is being used. At other times, it is being stored on the volume in encrypted form.
* All data on disk would therefore be ciphertext
* If EC2 instance ever moves from one host to another, the decrypted copy in memory is discarded.
* Snapshots created from volume are encrypted and volumes created from the snapshot would also be encrypted using the same key.

Exam powerups

* AWS accounts can be set to encrypt by default - Default CMK
  * Or choose a CMK to use
* CMK is not used directly. It is used to generate 1 unique DEK per volume.
* Snapshots & future volumes use the same DEK.
* Can't change a volume to NOT be encrypted
  * Could mount a non-encrypted volume and copy data across
* OS isn't aware of the encryption, no performance loss. The volume itself is encrypted using AES-256. Occurs between EC2 host and EBS system. From it's perspective, it is not using disk encryption.
* If OS needs to perform encryption or hold keys or use a different algorithm from AES-256, then we need full disk encryption at the OS level.
  * Can be applied to an encrypted or non encrypted EBS volume
* EBS encryption is really effieient
  * No worrying about keys
  * Doesn't cost anything
  * No performance penalty for using it (OS level will have performance hit)
