:original_name: kms_02_0217.html

.. _kms_02_0217:

Updating a Secret
=================

Function
--------

This API is used to update the metadata of a specified secret.

Constraints
-----------

This API can be used to modify only the secret metadata, not the secret value.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

PUT /v1/{project_id}/secrets/{secret_name}

.. table:: **Table 1** URI parameters

   =========== ========= ====== ============
   Parameter   Mandatory Type   Description
   =========== ========= ====== ============
   project_id  Yes       String Project ID.
   secret_name Yes       String Secret name.
   =========== ========= ====== ============

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                       |
   +==============+===========+========+===================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token, which can be obtained by calling the IAM API. (The token is the value of **X-Subject-Token** in the response header.) |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Application/JSON                                                                                                                  |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | X-Language   | Yes       | String | Error code language of the API response. The value must be **en-us**.                                                             |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                             |
   +=============+===========+========+=========================================================================================================================================================================================================================+
   | kms_key_id  | No        | String | ID of the KMS CMK used to encrypt secret values. The CMK of a secret can be updated. Secret versions after the update use the new CMK for encryption. Secret versions before the update use the old CMK for decryption. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String | Description of a secret Constraints: The value contains 2048 bytes.                                                                                                                                                     |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameter

   +-----------+-----------------------------------------------------+-------------+
   | Parameter | Type                                                | Description |
   +===========+=====================================================+=============+
   | secret    | :ref:`Secret <kms_02_0217__response_secret>` object | Secret      |
   +-----------+-----------------------------------------------------+-------------+

.. _kms_02_0217__response_secret:

.. table:: **Table 5** Secret parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================+
   | id                    | String                | Secret ID                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Secret name.                                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                | Secret status. Its value can be:                                                                                                               |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **ENABLED**                                                                                                                                    |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **DISABLED**                                                                                                                                   |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **PENDING_DELETE**                                                                                                                             |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **FROZEN**                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id            | String                | ID of the KMS CMK used to encrypt secret values                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description of a secret                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Secret creation time. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Time when a secret was last updated. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_delete_time | Long                  | Time when a secret will be deleted as scheduled. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970). |
   |                       |                       |                                                                                                                                                |
   |                       |                       | If a secret is not in **Pending deletion** state, the value of this parameter is **null**.                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Update the secret named **test_secret**. Specifically, change the KMS encryption key ID to **0d0466b0-e727-4d9c-b35d-f84bb474a37f** and the secret description to **update description**.

.. code-block:: text

   PUT https://{csms_endpoint}/v1/{project_id}/secrets/test_secret
   {
     "kms_key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
     "description" : "update description"
   }

Example Response
----------------

.. code-block::

   {
     "secret" : {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "name" : "test_secret",
       "state" : "ENABLED",
       "kms_key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
       "description" : "update description",
       "create_time" : 1581507580000,
       "update_time" : 1581507580000,
       "scheduled_delete_time" : 1581507580000
     }
   }

Status Code
-----------

=========== ====== ==================
Status Code Status Description
=========== ====== ==================
200         OK     Request succeeded.
=========== ====== ==================

Error Code
----------

For details, see :ref:`Error Code <kms_02_8887>`.
