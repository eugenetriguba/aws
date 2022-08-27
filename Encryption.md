## Encryption Approaches

### Encryption at Rest

* Designed to protect against physical theft and tampering
* i.e. Encrypted hardware on a laptop
* Used a lot in Cloud environments where data is stored on a shared hard drive and done so in an encrypted form.
* Generally one party involved

### Encryption at Transit

* Generally two or more parties (individual or systems) involved
* Encryption tunnel on the raw data so anyone looking at the data from the outside sees a stream of scrambled data.

## Concepts

* Plaintext: Unencrypted data (not necessarily text, can be binary image data)
* Algorithm: Piece of math that takes plaintext and an encryption key and generates encrypted data
  * Blowfish, AES, RC4, DES, RC5, RC6
* Key: A password but can be much more complex
* Ciphertext: Encrypted data

For encryption, an algorithm, using a key, takes plaintext and uses that those to create ciphertext.

## Symmetric Encryption

* Two parties agree on an algorithm to use.
* Uses the plaintext and key, ciphertext is generated. Using the same key, the other party decrypts the ciphertext into plaintext.
* Same key is used for encrypted and decryption.
* Find a way to get the other party a copy of the key.
* Great for local file encryption or encryption on a laptop but not so great when data needs to be transferred to remote parties because the transfer of the key is tricky.

## Asymmetric Encryption

* Two parties agree on an asymmetric algorithm to use.
* Public/Private key.
* Public key can be used to generate the ciphertext and the private key can be used to take ciphertext and generate the corresponding plaintext.
* Generally used when two or more parties are involved and those parties have never physically met before.
* The public key can be freely shared since only the private key can decrypt ciphertext generated with the public key.
  * SSL/TLS
  * SSH
  * PGP
* Computationally much more difficult
* Often used initially to communicate the symmetric key and then the symmetric key is used from there on.

## Signing

* Received encrypted document and want to confirm a) we've received it and b) we agree to it.
* Respond with a simple OK message. Problem is anyone can encrypt and send a message via the public key and we wouldn't be aware who it is from. Encryption does not prove identity.
* Using private key, can sign a message and sent to the other party. The other party can use the public key to prove whether the message was signed with the original private key.
* Signing is generally done to verify identity, as long as we can be sure that the public key belongs to the original party. This is generally done by putting the public key on something like the parties twitter account or website.

## Steganography

* If you encrypt data, someone will know that you've encrypted data.
* Method of hiding something in something else. Invisible ink is a physical example.
* We could generate some ciphertext and hide it in a puppy image. The other party then would know to extract some data from the image.
* Effective steganography algorithms make it almost impossible to find the hidden data unless you know a certain key, number, or pattern.
* Encrypt some data using the other parties public key, take that ciphertext and use steganography to embed it in something that wouldn't be tied back to the sending party, and then the party could use steganography to extract the ciphertext and decrypt it using the private key. Then it could be following in reverse to signal an OK but have the party with the private key also sign it.
