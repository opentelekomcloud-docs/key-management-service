:original_name: kms_02_0214.html

.. _kms_02_0214:

Creating a Secret
=================

Function
--------

This API is used to create a secret and store the secret value in the initial secret version.

Secret values are encrypted and stored in secret versions. A version can have multiple statuses. Versions without any statuses are regarded as deprecated versions and will be automatically deleted by CSMS. A maximum of 20 secrets can be created. If there are more than 20 created secrets, CSMS automatically deletes the earliest unused secret version.

The initial version is marked by the **SYSCURRENT** status tag.

Constraints
-----------

You can use a symmetric customer master key (CMK) to encrypt a secret. If the **kms_key_id** parameter is not specified, the default master key **csms/default** will be used to encrypt secrets. The default key is automatically created by CSMS.

To use a user-defined key to encrypt secrets, you need to have the kms:dek:create permission for the key.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/secrets

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type             | Description                                                                                                                                                                                                       |
   +=====================+=================+==================+===================================================================================================================================================================================================================+
   | name                | Yes             | String           | Secret name.                                                                                                                                                                                                      |
   |                     |                 |                  |                                                                                                                                                                                                                   |
   |                     |                 |                  | Constraint: The value can contain 1 to 64 characters and must match the regular expression **^[a-zA-Z0-9._-]{1,64}$**.                                                                                            |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id          | No              | String           | ID of the KMS CMK used to encrypt secrets. If this parameter is not specified, the default master key **csms/default** will be used. The default key is automatically created by CSMS.                            |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description         | No              | String           | Description of a secret.                                                                                                                                                                                          |
   |                     |                 |                  |                                                                                                                                                                                                                   |
   |                     |                 |                  | Constraints: The value contains 2048 bytes.                                                                                                                                                                       |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_binary       | No              | String           | Plaintext of a binary secret in Base64 format. CSMS encrypts it and stores it in the initial version of the secret.                                                                                               |
   |                     |                 |                  |                                                                                                                                                                                                                   |
   |                     |                 |                  | Type: binary data object in Base64 format                                                                                                                                                                         |
   |                     |                 |                  |                                                                                                                                                                                                                   |
   |                     |                 |                  | Constraints: You must configure either **secret_binary** or **secret_string**. The maximum size is 32 KB.                                                                                                         |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_string       | No              | String           | Plaintext of a binary secret in text format. CSMS encrypts it and stores it in the initial version of the secret.                                                                                                 |
   |                     |                 |                  |                                                                                                                                                                                                                   |
   |                     |                 |                  | Constraints: You must configure either **secret_binary** or **secret_string**. The maximum size is 32 KB.                                                                                                         |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_subscriptions | No              | Array of strings | Subscribed event list. Currently, only one event can be subscribed to. When an event containing a basic event is triggered, a message is sent to the topic corresponding to the event, for example, **pocEvent**. |
   +---------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameter

   +-----------+-----------------------------------------------------+-------------+
   | Parameter | Type                                                | Description |
   +===========+=====================================================+=============+
   | secret    | :ref:`Secret <kms_02_0214__response_secret>` object | Secret      |
   +-----------+-----------------------------------------------------+-------------+

.. _kms_02_0214__response_secret:

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

Create a secret named **demo**. Encrypt the value of secret **this is a demo secret string** using the KMS key whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/secrets
   {
     "name" : "demo",
     "kms_key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
     "secret_string" : "this is a demo secret string"
   }

Example Response
----------------

.. code-block::

   {
     "secret" : {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "name" : "test",
       "state" : "ENABLED",
       "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
       "description" : "description",
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
