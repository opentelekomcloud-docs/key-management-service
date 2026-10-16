:original_name: ValidateSignature.html

.. _ValidateSignature:

Authenticating a Signature
==========================

Function
--------

-  This API uses the private key of an asymmetric key to verify a signature.

Constraints
-----------

-  Only the asymmetric key whose **key_usage** is **SIGN_VERIFY** can be used for signature verification.

URI
---

POST /v1.0/{project_id}/kms/verify

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. The token can be obtained by calling the IAM API. (The token is the value of **X-Subject-Token** in the response header.) |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | application/json                                                                                                                      |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                               |
   +===================+=================+=================+===========================================================================================================================================================================================+
   | key_id            | Yes             | String          | The value can be a key ID, alias (**key_alias**), or URN.                                                                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                           |
   |                   |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                   |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                   |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   |                   |                 |                 |                                                                                                                                                                                           |
   |                   |                 |                 |    .. note::                                                                                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                           |
   |                   |                 |                 |       The **alias_urn** generated during key alias creation is the URN.                                                                                                                   |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message           | Yes             | String          | Message digest or message to be signed. The message must be encoded using Base64 and be less than 4,096 bytes.                                                                            |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature         | Yes             | String          | Signature value to be verified, which is encoded using Base64.                                                                                                                            |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_algorithm | Yes             | String          | Signature algorithm. Possible values are as follows:                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                           |
   |                   |                 |                 | -  **RSASSA_PSS_SHA_256**                                                                                                                                                                 |
   |                   |                 |                 | -  **RSASSA_PSS_SHA_384**                                                                                                                                                                 |
   |                   |                 |                 | -  **RSASSA_PSS_SHA_512**                                                                                                                                                                 |
   |                   |                 |                 | -  **RSASSA_PKCS1_V1_5_SHA_256**                                                                                                                                                          |
   |                   |                 |                 | -  **RSASSA_PKCS1_V1_5_SHA_384**                                                                                                                                                          |
   |                   |                 |                 | -  **RSASSA_PKCS1_V1_5_SHA_512**                                                                                                                                                          |
   |                   |                 |                 | -  **ECDSA_SHA_256**                                                                                                                                                                      |
   |                   |                 |                 | -  **ECDSA_SHA_384**                                                                                                                                                                      |
   |                   |                 |                 | -  **ECDSA_SHA_512**                                                                                                                                                                      |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_type      | No              | String          | Message type. The default value is **DIGEST**. Possible values are as follows:                                                                                                            |
   |                   |                 |                 |                                                                                                                                                                                           |
   |                   |                 |                 | -  **DIGEST** (message digest)                                                                                                                                                            |
   |                   |                 |                 | -  **RAW** (original message)                                                                                                                                                             |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence          | No              | String          | A 36-byte serial number of a request message. Example: **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                           |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameters

   +-----------------+--------+-------------------------------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                                               |
   +=================+========+===========================================================================================+
   | key_id          | String | CMK ID                                                                                    |
   +-----------------+--------+-------------------------------------------------------------------------------------------+
   | signature_valid | String | Whether the signature is valid. Its value can be **true** (valid) or **false** (invalid). |
   +-----------------+--------+-------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   {
     "key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
     "signing_algorithm" : "RSASSA_PKCS1_V1_5_SHA_256",
     "signature" : "jFUqQESGBc0j6k9BozzrP9YL4qk8/W9DZRvK6XXX...",
     "message" : "MmFiZWE0ZjI3ZGIxYTkzY2RmYmEzM2YwMTA1YmJjYw=="
   }

Example Response
----------------

**Status code: 200**

The request has succeeded.

.. code-block::

   {
     "key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
     "signature_valid" : "true"
   }

Status Codes
------------

=========== ====== ==================
Status Code Status Description
=========== ====== ==================
200         OK     Request succeeded.
=========== ====== ==================
