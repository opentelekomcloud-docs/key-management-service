:original_name: dew_01_7775.html

.. _dew_01_7775:

Key Types
=========

Master Key
----------

A master key, the highest level of keys in a cryptographic system, generates and manages other keys, including session keys and data encryption keys, or directly encrypts important data. It is vital to protect its security and confidentiality. Once a master key is leaked, the entire cryptographic system may be severely threatened.

**A master key features the following**:

-  **High security**: A master key is generally the most sensitive key in a system and needs to be strictly protected. It is usually stored in a secure hardware device, such as an HSM.
-  **Long-term use**: A master key has a long lifecycle and will not be frequently changed to ensure system stability and consistency.
-  **Multi-usage**: A master key can be used for various encryption operations, including subkey generation, data encryption, and signature verification.
-  **Uniqueness**: A master key is unique in a cryptographic system. In a distributed system, each node or region may have its own master key.

Master keys include **custom keys** and **default keys**. You can create, view, enable, disable, schedule the deletion of, and cancel the deletion of custom keys.

Custom keys can be categorized into symmetric keys and asymmetric keys.

-  Symmetric keys are most commonly used for data encryption protection.
-  Asymmetric keys are used for digital signature verification or sensitive information encryption in systems where the trust relationship is not mutual. An asymmetric key consists of a public key and a private key. The public key can be sent to anyone. The private key must be securely stored and only accessible to trusted users.
-  An asymmetric key can be used to generate and verify a signature. To securely transfer data, a signer sends the public key to a receiver, uses the private key to sign data, and then sends the data and signature to the receiver. The receiver can use the public key to verify the signature.

Key Algorithms Supported by KMS
-------------------------------

.. table:: **Table 1** Key algorithms supported by KMS

   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key Type       | Algorithm Type | Key Specifications | Description                        | Application Scenario                                                                                                                                                                                                  |
   +================+================+====================+====================================+=======================================================================================================================================================================================================================+
   | Symmetric key  | AES            | AES_256            | AES symmetric key                  | -  Data encryption and decryption                                                                                                                                                                                     |
   |                |                |                    |                                    | -  DEKs encryption and decryption                                                                                                                                                                                     |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |    .. note::                                                                                                                                                                                                          |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |       You can encrypt and decrypt a small amount of data using the online tool on the console.                                                                                                                        |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |       You need to call APIs to encrypt and decrypt a large amount of data.                                                                                                                                            |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Digest key     | SHA            | -  HMAC_256        | Digest key                         | -  Data tampering prevention                                                                                                                                                                                          |
   |                |                | -  HMAC_384        |                                    | -  Data integrity verification                                                                                                                                                                                        |
   |                |                | -  HMAC_512        |                                    |                                                                                                                                                                                                                       |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Asymmetric key | RSA            | -  RSA_2048        | RSA asymmetric password            | -  Digital signature and signature verification                                                                                                                                                                       |
   |                |                | -  RSA_3072        |                                    | -  Data encryption and decryption                                                                                                                                                                                     |
   |                |                | -  RSA_4096        |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |    .. note::                                                                                                                                                                                                          |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |       Asymmetric keys are applicable to signature and signature verification scenarios. Asymmetric keys are not efficient enough for data encryption. Symmetric keys are suitable for encrypting and decrypting data. |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                | ECC            | -  EC_P256         | Elliptic curve recommended by NIST | Digital signature and signature verification                                                                                                                                                                          |
   |                |                | -  EC_P384         |                                    |                                                                                                                                                                                                                       |
   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
