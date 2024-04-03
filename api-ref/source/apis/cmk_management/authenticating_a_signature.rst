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
-  SM2 keys can only be used to sign message digests. According to the GBT32918 standard, in SM2 signature value calculation, the message digest is not an SM3 digest calculated based on the original message. Instead, it is a digest of the concatenation of **Z(**\ *A*\ **)** and **M**. Here **M** indicates the original message to be signed, and **Z(**\ *A*\ **)** indicates the hash value of user *A* defined in GBT32918.

URI
---

POST /v1.0/{project_id}/kms/verify

.. table:: **Table 1** URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. The token can be obtained by calling the IAM API. (The token is the value of **X-Subject-Token** in the response header.) |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                              |
   +===================+=================+=================+==========================================================================================================================================================================+
   | key_id            | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$** Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message           | Yes             | String          | Message digest or message to be signed. The message must be encoded using Base64 and be less than 4096 bytes.                                                            |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature         | Yes             | String          | Signature value to be verified, which is encoded using Base64.                                                                                                           |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_algorithm | Yes             | String          | Signature algorithm. Its value can be:                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                          |
   |                   |                 |                 | -  RSASSA_PSS_SHA_256                                                                                                                                                    |
   |                   |                 |                 | -  RSASSA_PSS_SHA_384                                                                                                                                                    |
   |                   |                 |                 | -  RSASSA_PSS_SHA_512                                                                                                                                                    |
   |                   |                 |                 | -  RSASSA_PKCS1_V1_5_SHA_256                                                                                                                                             |
   |                   |                 |                 | -  RSASSA_PKCS1_V1_5_SHA_384                                                                                                                                             |
   |                   |                 |                 | -  RSASSA_PKCS1_V1_5_SHA_512                                                                                                                                             |
   |                   |                 |                 | -  ECDSA_SHA_256                                                                                                                                                         |
   |                   |                 |                 | -  ECDSA_SHA_384                                                                                                                                                         |
   |                   |                 |                 | -  ECDSA_SHA_512                                                                                                                                                         |
   |                   |                 |                 | -  SM2DSA_SM3                                                                                                                                                            |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_type      | No              | String          | Message type. The default value is **DIGEST**. Its value can be:                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                          |
   |                   |                 |                 | -  **DIGEST** (message digest)                                                                                                                                           |
   |                   |                 |                 | -  **RAW** (original message)                                                                                                                                            |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence          | No              | String          | 36-byte serial number of a request message Example: **919c82d4-8046-4722-9094-35c3c6524cff**                                                                             |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------+--------+-------------------------------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                                               |
   +=================+========+===========================================================================================+
   | key_id          | String | CMK ID                                                                                    |
   +-----------------+--------+-------------------------------------------------------------------------------------------+
   | signature_valid | String | Whether the signature is valid. Its value can be **true** (valid) or **false** (invalid). |
   +-----------------+--------+-------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 6** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 401**

.. table:: **Table 7** Response body parameter

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 8** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 10** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 404**

.. table:: **Table 11** Response body parameters

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 12** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 500**

.. table:: **Table 13** Response body parameter

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 14** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 502**

.. table:: **Table 15** Response body parameters

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 16** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 504**

.. table:: **Table 17** Response body parameters

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   error     Object Error message.
   ========= ====== ==============

.. table:: **Table 18** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

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

Status Code
-----------

+-------------+---------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                       |
+=============+===================================================================================================+
| 200         | The request has succeeded.                                                                        |
+-------------+---------------------------------------------------------------------------------------------------+
| 400         | Invalid request parameters.                                                                       |
+-------------+---------------------------------------------------------------------------------------------------+
| 401         | Username and password are required to access the page requested.                                  |
+-------------+---------------------------------------------------------------------------------------------------+
| 403         | Authentication failed.                                                                            |
+-------------+---------------------------------------------------------------------------------------------------+
| 404         | The requested resource does not exist or is not found.                                            |
+-------------+---------------------------------------------------------------------------------------------------+
| 500         | Internal service error.                                                                           |
+-------------+---------------------------------------------------------------------------------------------------+
| 502         | Failed to complete the request. The server receives an invalid response from the upstream server. |
+-------------+---------------------------------------------------------------------------------------------------+
| 504         | Gateway timed out.                                                                                |
+-------------+---------------------------------------------------------------------------------------------------+
