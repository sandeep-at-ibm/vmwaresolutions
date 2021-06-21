---

copyright:

  years:  2019, 2021

lastupdated: "2020-04-21"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Encryption overview
{: #htdc-hpcs-encryption-overview}

## Terms
{: #htdc-hpcs-encryption-overview-terms}

The following terms are used in this documentation:
* Symmetric key cryptography - This method of encryption uses the same encryption key is used to both encrypt and decrypt the data and is used primarily to protect data at rest.
* Asymmetric key cryptography - This method of encryption uses a pair of keys, public and private, for the encryption and decryption of the data. Asymmetric keys are primarily used to secure data-in-motion. Both keys are related to each other and created at the same time.
 * Public Key - this key is used to encrypt the data and can be freely given as it is used to encrypt data, not to decrypt it.
 * Private Key - this key is used to decrypt the data that the public key encrypted. This key must be safeguarded as it is the only key that can decrypt the encrypted data.
* Data encryption key (DEK) - An encryption key whose function is to encrypt and decrypt data.
* Key encryption key (KEK) - An encryption key, which is used to encrypt and decrypt the DEK.
* Key management application programming interface (KM API) - An application interface that is designed to securely retrieve and communicate encryption keys from a key management server to the client that requests the keys.
* Certificate authority (CA) - An entity that creates public and private keys, creates certificates, verifies certificates, and does other PKI functions.
* Transport layer security (TLS) - A cryptographic protocol that provides security, through mutual authentication, for data-in-motion over a network.
* Key Manager (KM) - The software that manages the key lifecycle.
* Key Management System (KMS) - A system that hosts the key manager and key storage database.
* Envelope encryption - Envelope encryption is the technique of encrypting data with a DEK and then encrypting the DEK with a root key that you can fully manage.

## Encryption overview
{: #htdc-hpcs-encryption-overview-steps}

The following sequence is a step-by-step example of how an authorized user accesses encrypted data:

1. A user requests to access encrypted data.
2. The database, application, file system, or storage then sends a DEK retrieval request to the KM API.
3. The KM API and KM verify each other’s certificates, the KM API sends a certificate to the KM for verification. The KM then checks the certificate against the CA for authentication. After the KM API certificate is verified, the KM sends its certificate to the KM API for authentication and acceptance.
4. After the certificates are accepted, a secure TLS connection is established between the KM API and the KM.
5. The KM then retrieves the requested DEK from the key storage database and decrypts the DEK with the KEK.
6. The KM sends the DEK to the KM API over the encrypted TLS session.
7. The KM API then sends the DEK to the database, application, file system, or storage.
8. The database, application, file system, or storage then sends the plain text information to the user.

## Key lifecycle
{: #htdc-hpcs-encryption-overview-lifecycle}

Keys have the following lifecycle:
* Key Creation - The encryption key is created and stored on the key management server. The key manager creates the encryption key by using a cryptographically secure random bit generator and stores the key, along with its attributes, in the key storage database.
* Key Use  - The key manager allows an activated key to be retrieved by authorized systems and users. The key manager also rolls the key through.
* A previously established schedule or allow a manual roll by an administrator.
* Key Revocation - An administrator can request the key manager to revoke a key so that it is no longer used for encryption requests.
* Back Up - Encryption keys need to be recoverable in case they need to be reactivated for use in decrypting data that it originally encrypted.
* Key Deletion - If a key is no longer required, an administrator can choose to delete the key entirely from the key storage database of the encryption key manager. When the key is deleted, the data becomes unrecoverable since it is impossible to re-create the key.

## Key best practice
{: #htdc-hpcs-encryption-overview-best}

The following are considered to be best practices in key management:
* Separation of duties - The implementation of separation of duties is critical for encryption key management, and to prevent unwanted access to protected data. The person who manages the encryption keys must not have access to the protected data, and vice versa.
* Dual control - Dual Control requires that at least two or more individuals control a single process, so no single person is able to access or use the cryptographic keys.
* Split Knowledge - This concept ensures that no one person knows the complete value of an encryption key. If passphrases are used to create encryption keys, then no single person would know the entire passphrase. Therefore, two or more people would need to be available to create or re-create an encryption key.

**Next topic:** [vCenter Server encryption options](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-encryption-options)

## Related links
{: #htdc-hpcs-encryption-overview-related}

* [HyTrust® DataControl®](https://www.hytrust.com/products/datacontrol-workload-encryption/){:external}
