:original_name: kms_01_0047.html

.. _kms_01_0047:

Functions
=========

KMS provides the following functions:

-  Manages custom keys.

   You can perform the following operations on custom keys on the KMS console or via APIs:

   -  Creating, querying, enabling, disabling, scheduling the deletion of, and canceling the deletion of custom keys
   -  Importing keys and deleting key material
   -  Modifying the name and description of a custom key
   -  Using the online tool to encrypt and decrypt small-size data
   -  Creating, querying, and revoking a grant
   -  Adding, searching for, editing, and deleting tags
   -  Enabling key rotation

-  Creates, encrypts, and decrypts DEKs, and retires a grant on a key.

   By calling APIs, you can create, encrypt, and decrypt DEKs, and retire a grant on a key. For details, see the *Key Management Service API Reference*.

-  Generates hardware true random numbers.

   You can generate 512-bit hardware true random numbers using a KMS API. The 512-bit hardware true random numbers can be used as or serve as basis for keys and encryption parameters. For details, see .

Key Algorithms Supported by KMS
-------------------------------

Symmetric keys created on the KMS console use the AES-256 algorithm. Asymmetric keys created by KMS support the RSA and ECC algorithms.

.. table:: **Table 1** Key algorithms supported by KMS

   +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key Type       | Algorithm Type | Key Specifications | Description                        | Application Scenario                                                                                                                                                                                                  |
   +================+================+====================+====================================+=======================================================================================================================================================================================================================+
   | Symmetric key  | AES            | AES_256            | AES symmetric key                  | -  Data encryption and decryption                                                                                                                                                                                     |
   |                |                |                    |                                    | -  DEKs encryption and decryption                                                                                                                                                                                     |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |    .. note::                                                                                                                                                                                                          |
   |                |                |                    |                                    |                                                                                                                                                                                                                       |
   |                |                |                    |                                    |       You can encrypt and decrypt a small amount of data using the the online tool on the console.                                                                                                                    |
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

:ref:`Key wrapping algorithms <kms_01_0047__table35495333248>` describes the cryptographic key wrapping algorithms supported by imported keys.

.. _kms_01_0047__table35495333248:

.. table:: **Table 2** Key wrapping algorithms

   +--------------------+----------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Algorithm          | Description                                                                      | Example Value                                             |
   +====================+==================================================================================+===========================================================+
   | RSAES_OAEP_SHA_256 | RSA cryptographic algorithm that uses OAEP and has the **SHA-256** hash function | The **RSAES_OAEP_SHA_256** encryption key is recommended. |
   +--------------------+----------------------------------------------------------------------------------+-----------------------------------------------------------+
