:original_name: kms_01_0001.html

.. _kms_01_0001:

Functions
=========

KMS is a secure, reliable, and easy-to-use cloud service that helps users create, manage, and protect keys in a centralized manner.

It uses Hardware Security Modules (HSMs) to protect keys. All keys are protected by root keys in HSMs to avoid key leakage. The HSM module meets the FIPS 140-2 Level 3 security requirements.

It also controls access to keys and records all operations on keys with traceable logs. In addition, it provides use records of all keys, meeting your audit and regulatory compliance requirements.


Functions
---------

-  On the KMS console, you can:

   -  Create, query, enable, and disable CMKs, as well as schedule and cancel CMK deletion.
   -  Modify the alias and description of CMKs.
   -  Use the online tool to encrypt and decrypt small-size data.
   -  Import keys and delete key material.
   -  Add, search for, edit, and delete tags.
   -  Create, cancel, and query grants.

-  You can use the API to perform the following operations:

   -  Create, encrypt, or decrypt DEKs.
   -  Retire grants.

   For details, see *Key Management Service API Reference*.

-  Generate hardware true random numbers.

   You can generate 512-bit hardware true random numbers using a KMS API. The numbers can be used as a basis for key materials or as encryption parameters. For details, see the Key Management Service API Reference.

Key Algorithms Supported by KMS
-------------------------------

Symmetric keys created on the KMS console use the AES algorithm. Asymmetric keys created by KMS support the RSAand ECC algorithms.

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

:ref:`Table 2 <kms_01_0001__table123192815372>` describes the encryption and decryption algorithms supported for user-imported keys.

.. _kms_01_0001__table123192815372:

.. table:: **Table 2** Key wrapping algorithms

   +-----------------------+--------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Algorithm             | Description                                                        | Configuration                                                                                                   |
   +=======================+====================================================================+=================================================================================================================+
   | RSAES_OAEP_SHA_256    | RSA algorithm that uses OAEP and has the **SHA-256** hash function | Select an algorithm based on your HSM functions.                                                                |
   |                       |                                                                    |                                                                                                                 |
   |                       |                                                                    | If your HSM supports the **RSAES_OAEP_SHA_256** algorithm, use **RSAES_OAEP_SHA_256** to encrypt key materials. |
   +-----------------------+--------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
