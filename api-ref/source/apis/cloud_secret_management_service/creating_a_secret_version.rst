:original_name: kms_02_0223.html

.. _kms_02_0223:

Creating a Secret Version
=========================

Function
--------

This API is used to create a new version of a secret to encrypt and keep the new value of the secret. By default, the created secret version in **SYSCURRENT** state. The previous version is in **SYSPREVIOUS** state. You can configure the **VersionStage** to overwrite the default settings.

Constraints
-----------

-  The CSMS console only uses the **secret_string** field. To add a binary secret to the **secret_binary** field, you must use an SDK or API.
-  A secret can have up to 20 versions.
-  You can only add versions to enabled secrets.
-  Secret versions are numbered v1, v2, v3, and so on based on their creation time.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/secrets/{secret_name}/versions

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

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                          |
   +=================+=================+==================+======================================================================================================================+
   | secret_binary   | No              | String           | Value of a new secret. It will be encrypted and stored in the initial version of the secret.                         |
   |                 |                 |                  |                                                                                                                      |
   |                 |                 |                  | Type: binary data object in Base64 format                                                                            |
   |                 |                 |                  |                                                                                                                      |
   |                 |                 |                  | Constraints: You must configure either **secret_binary** or **secret_string**. The maximum size is 32 KB.            |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | secret_string   | No              | String           | Value of a new secret. It will be encrypted and stored in the initial version of the secret.                         |
   |                 |                 |                  |                                                                                                                      |
   |                 |                 |                  | Constraints: You must configure either **secret_binary** or **secret_string**. The maximum size is 32 KB.            |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | version_stages  | No              | Array of strings | Status of a new secret version. If this parameter is not specified, the default version **SYSCURRENT** will be used. |
   |                 |                 |                  |                                                                                                                      |
   |                 |                 |                  | Constraint: The array can contain 1 to 12 items. The stage length is 1 to 64 bytes.                                  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameter

   +------------------+-----------------------------------------------------------------------+-----------------------------+
   | Parameter        | Type                                                                  | Description                 |
   +==================+=======================================================================+=============================+
   | version_metadata | :ref:`VersionMetadata <kms_02_0223__response_versionmetadata>` object | Status of a secret version. |
   +------------------+-----------------------------------------------------------------------+-----------------------------+

.. _kms_02_0223__response_versionmetadata:

.. table:: **Table 5** VersionMetadata

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================================================================+
   | id                    | String                | ID of a secret version. A secret cannot have duplicate version IDs.                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Secret version creation time. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id            | String                | ID of the KMS CMK used to encrypt secret values.                                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_name           | String                | Secret name.                                                                                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_stages        | Array of strings      | Status list of a secret version. A status tag can be used for only one version of each secret. For example, if you add the status tag used by version A to version B, the tag will be moved from version A to version B. |
   |                       |                       |                                                                                                                                                                                                                          |
   |                       |                       | If the **version_stage** parameter is not specified, the status of the latest version will be **SYSCURRENT** by default.                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Create a secret version for secret **test**. The secret value is **secret_string**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/secrets/test/versions
   {
     "secret_string" : "secret_string"
   }

Example Response
----------------

.. code-block::

   {
     "version_metadata" : {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
       "create_time" : 1581507580000,
       "secret_name" : "secret-name-demo",
       "version_stages" : [ "pending", "used" ]
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
