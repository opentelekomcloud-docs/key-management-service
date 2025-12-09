:original_name: Sign.html

.. _Sign:

Signing Data
============

Function
--------

-  This API is used to use the private key of an asymmetric key to digitally sign a message or digest.

Constraints
-----------

-  Only the asymmetric key whose **key_usage** is **SIGN_VERIFY** can be used for signature.

URI
---

POST /v1.0/{project_id}/kms/sign

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                    |
   +==============+===========+========+================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API. (The token is the value of **X-Subject-Token** in the response header.) |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | application/json                                                                                                               |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+

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
   | message           | Yes             | String          | Message digest or message to be signed. The message must be encoded using Base64 and be less than 4096 bytes.                                                                             |
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
   | sequence          | No              | String          | A 36-byte serial number of a request message. Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                               |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ==============================================
   Parameter Type   Description
   ========= ====== ==============================================
   key_id    String CMK ID
   signature String Signature value, which is encoded using Base64
   ========= ====== ==============================================

**Status code: 400**

.. table:: **Table 5** Response body parameter

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

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 8** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 403**

.. table:: **Table 9** Response body parameter

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 10** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 404**

.. table:: **Table 11** Response body parameter

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 12** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 500**

.. table:: **Table 13** Response body parameter

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 14** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 502**

.. table:: **Table 15** Response body parameter

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 16** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

**Status code: 504**

.. table:: **Table 17** Response body parameter

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   error     Object Error message
   ========= ====== =============

.. table:: **Table 18** ErrorDetail

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error information
   ========== ====== =================

Example Request
---------------

The following uses the RSASSA_PKCS1_V1_5_SHA_256 signature algorithm to sign the raw message.

.. code-block::

   {
    "key_id": "968d6cf0-feb6-42c6-bb30-d69f74f2d5f9",
    "message": "aGVsbG8g",
    "signing_algorithm": "RSASSA_PSS_SHA_256",
    "message_type": "RAW"
   }

The following uses the RSASSA_PKCS1_V1_5_SHA_256 signature algorithm to sign the digest message.

.. code-block::

   {
    "key_id": "968d6cf0-feb6-42c6-bb30-d69f74f2d5f9",
    "message": "iNQmb9TmM40TuEX88olXnSCciXgjuSF9o+Fhk28DFYK=",
    "signing_algorithm": "RSASSA_PSS_SHA_256",
    "message_type": "DIGEST"
   }

Example Response
----------------

**Status code: 200**

The following shows that the request for signing the raw message using the RSASSA_PKCS1_V1_5_SHA_256 signature algorithm is successful.

.. code-block::

   {
    "key_id": "968d6cf0-feb6-42c6-bb30-d69f74f2d5f9",
    "signature": "BqhL4PFPMNIXyEld3qviF7uqqnqlm9TcVCUN9FTRCr6KGreHIvwE4YuAc+eLWVSCGRd3bQHhDOQ9GlWjixGengwBix1RPP0qxtn2p7kQxkC2j76VjKCwqAsAy4MyxjN8RNOdnVCpOObDGoLxPHxUwNvSqZ6GxQKZ4cHPXVH0r/jH9csgk6IUr6ATyto+IcNWSvD03LfaNRQ+Rvc5tOzNFpFrMnVl319UG9ANscq1ne67VW2uQIf74Osg9DYzbJTf/xqW5GFi3ZoeQUu+gMxwgQp3pkuYhygjw6a8Qy9ZNMHmWnY199SzHrxgIq3ymQzUU5zrikKMColX2goPXf5fxQ=="
   }

The following shows that the request for signing the digest message using the RSASSA_PKCS1_V1_5_SHA_256 signature algorithm is successful.

.. code-block::

   {
    "key_id": "968d6cf0-feb6-42c6-bb30-d69f74f2d5f9",
    "signature": "M8Gqrm7EyyCPckMs90D7IOlUPCMHhoBh+nz9ySvdbOi7JMrl0ei+2lb+CQ2ZJN+pu7mftotq7/sHt0wWsDl8IOywYSBtWEmLW6AHnEPMykG/A9/Dp3kRuuKFoouCzWXeZyhIrzRUunAK5j5njcY/yTf6T8M+zBy1nAApb8WcHUen9/j7+X348iOnsSuWNVfXxy3NX41v9kLn6x115UDA/798VLSoMbsjcXKgdf/3GoZRYjcHxiX6s71/RWsQYme68qQN2B0q8Y9lk6rQxrw/AXHFoeaphYb7PriURRx0GxhOEEHb/9Tcr39Zlh3bbl/2aF3ytJORWIqatLtqgJ4uEA=="
   }

Status Codes
------------

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
