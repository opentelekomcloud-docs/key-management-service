:original_name: kms_01_7775.html

.. _kms_01_7775:

Key Types
=========

CMKs include custom keys and default keys. This section describes how to create, view, enable, disable, schedule the deletion, and cancel the deletion of custom keys.

Custom keys can be categorized into symmetric keys and asymmetric keys.

Symmetric keys are most commonly used for data encryption protection. Asymmetric keys are used for digital signature verification or sensitive information encryption in systems where the trust relationship is not mutual. An asymmetric key consists of a public key and a private key. The public key can be sent to anyone. The private key must be securely stored and only accessible to trusted users.

An asymmetric key can be used to generate and verify a signature. To securely transfer data, a signer sends the public key to a receiver, uses the private key to sign data, and then sends the data and signature to the receiver. The receiver can use the public key to verify the signature.

.. table:: **Table 1** Key algorithms supported by KMS

   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
   | Key Type       | Algorithm Type | Key Specifications | Description                        | Usage                                                                       |
   +================+================+====================+====================================+=============================================================================+
   | Symmetric key  | AES            | -  AES_256         | AES symmetric key                  | Encrypts and decrypts a small amount of data or data keys.                  |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
   | Asymmetric key | RSA            | -  RSA_2048        | RSA asymmetric password            | Encrypts and decrypts a small amount of data or creates digital signatures. |
   |                |                | -  RSA_3072        |                                    |                                                                             |
   |                |                | -  RSA_4096        |                                    |                                                                             |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
   |                | ECC            | -  EC_P256         | Elliptic curve recommended by NIST | Digital signature                                                           |
   |                |                | -  EC_P384         |                                    |                                                                             |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
