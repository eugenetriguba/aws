# SSL and TLS

- Provide privacy and data integrity between client and server.

- Privacy: communications are encrypted.
  - Process starts with asymmetric encryption architecture (server makes public key available for the client to use so it can encrypt traffic that only that server can decrypt) and then symmetric.

- Identity: server or client/server verified.
  - Most of the time, client is verifying the server via public key cryptography.

- Reliable connection: protect against alteration of data in transit.

## Phases

### Cipher Suites

A set of protocols used by TLS i.e. a key exchange, bulk encryption, and message encryption (HMAC) algorithm. For specific versions and types of these algorithms, this is known as a cipher suite.

In order to communicate, the client and server have to decide on a cipher suite to use. If the server doesn't support a list of supported cipher suites from the client, the connection fails.

1. Client HELLO
  a. SSL/TLS version, list of supported cipher suites, session ID, extensions.
2. Server HELLO
  a. SSL/TLS version, a cipher suite from the client list, and a server certificate
  b. At this point, the client and server have agreed on how to communicate and the client has the server certificate. The certificate contains the server's public key.

### Authentication

Ensure the server certificate is authentic, verifying the server as legitmate.

In the past, the server generates a public/private key pair and a Certificate Signing request (CSR) to the public CA generates a signed certificate. A public trusted certificate authority (CA) is something your OS/Browser trusts.

3. The client trusts the public CA. It makes sure that the certificate is valid (date and hasn't been revoked) and that the DNS name matches the name/names on the cert.

4. Client attempts to encrypt some random data and send it to the server using the public key within the certificate. This makes sure the server has the corresponding private key.
  a. If we're at this point and everything is good, the client trusts the server, the ID has been validated, and the client knows the server can decrypt data that is being sent.

### Key Exchange

Move from asymmetric to symmetric encryption in a secure way and begin encryption process. Symmetric encryption is less computationally intensive so it is ideal for the regular data transfers.

5. The client generates the pre-master key, encrypts it with the server's public key, and sends it to the server.

6. The server decrypts the pre-master key using its private key.

7. Both sides use the same pre-master key to generate the master secret which is used to generate the ongoing session keys which encrypt and decrypt data.

8. Both sides confirm the handshake and from then on, communications between the client and server are encrypted.

