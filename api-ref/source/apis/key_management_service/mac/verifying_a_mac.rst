:original_name: VerifyMac.html

.. _VerifyMac:

Verifying a MAC
===============

Function
--------

This API is used to verify a MAC.

Constraints
-----------

This API is supported only for keys whose **key_usage** is **GENERATE_VERIFY_MAC**.

URI
---

POST /v1.0/{project_id}/kms/verify-mac

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                |
   |                 |                 |                 |                                                                                                                                            |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is a token. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | application/json                                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================+
   | key_id          | Yes             | String          | ID of the key to be enabled. The value can be the key ID, alias (**key_alias**), or URN.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                 |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                 |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mac_algorithm   | Yes             | String          | MAC algorithm. Possible values are as follows:                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | -  **HMAC_SHA_256**                                                                                                                                                                       |
   |                 |                 |                 | -  **HMAC_SHA_384**                                                                                                                                                                       |
   |                 |                 |                 | -  **HMAC_SHA_512**                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | .. note::                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 |    The value must be the algorithm used for creating the key.                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message         | Yes             | String          | Message to be processed. The original message can contain 1 to 4,096 characters. Convert the original message to the Base64 format before importing it.                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mac             | Yes             | String          | MAC to be verified                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ============= ======= =======================
   Parameter     Type    Description
   ============= ======= =======================
   key_id        String  Key ID
   mac_algorithm String  MAC algorithm
   mac_valid     Boolean MAC verification result
   ============= ======= =======================

Example Request
---------------

.. code-block::

   {
     "key_id" : "826314dd-1b5b-4037-b976-5f9b7a17df46",
     "mac_algorithm" : "HMAC_SHA_256",
     "message" : "ZmRzYQ==",
     "mac" : "8549f9f5ef335184e23e6d477776f0fd338d02c59e48e52e8d81d158e2fc9262"
   }

Example Response
----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "mac_algorithm" : "HMAC_SHA_256",
     "key_id" : "826314dd-1b5b-4037-b976-5f9b7a17df46",
     "mac_valid" : true
   }

Status Codes
------------

=========== ==================
Status Code Description
=========== ==================
200         Request succeeded.
=========== ==================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
