:original_name: kms_02_0225.html

.. _kms_02_0225:

Querying the Secret Version and Value
=====================================

Function
--------

This API is used to query the information about a specified secret version and the plaintext secret value in the version. Only credentials in the Enabled state can be queried. The value of the latest secret version can be obtained via **/v1/{project_id}/secrets/{secret_name}/versions/latest**. (Set the **{version_id}** in the URL of the current API to **latest**).

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

GET /v1/{project_id}/secrets/{secret_name}/versions/{version_id}

.. table:: **Table 1** URI parameters

   =========== ========= ====== =================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =================
   project_id  Yes       String Project ID.
   secret_name Yes       String Secret name.
   version_id  Yes       String Secret version ID
   =========== ========= ====== =================

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

Response Parameters
-------------------

.. table:: **Table 3** Response body parameter

   +-----------+-------------------------------------------------------+----------------+
   | Parameter | Type                                                  | Description    |
   +===========+=======================================================+================+
   | version   | :ref:`Version <kms_02_0225__response_version>` object | Secret version |
   +-----------+-------------------------------------------------------+----------------+

.. _kms_02_0225__response_version:

.. table:: **Table 4** Version

   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                  | Description                                                                                                         |
   +=======================+=======================================================================+=====================================================================================================================+
   | version_metadata      | :ref:`VersionMetadata <kms_02_0225__response_versionmetadata>` object | Status of a secret version                                                                                          |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | secret_binary         | String                                                                | Plaintext of a binary secret in Base64 format. CSMS encrypts it and stores it in the initial version of the secret. |
   |                       |                                                                       |                                                                                                                     |
   |                       |                                                                       | Type: binary data object in Base64 format                                                                           |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | secret_string         | String                                                                | Plaintext of a binary secret in text format. CSMS encrypts it and stores it in the initial version of the secret.   |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0225__response_versionmetadata:

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

Query all versions of secret **test**.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/secrets/test/versions/bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e

Example Response
----------------

.. code-block::

   {
     "version" : {
       "version_metadata" : {
         "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
         "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
         "create_time" : 1581507580000,
         "secret_name" : "secret-name-demo",
         "version_stages" : [ "pending", "used" ]
       },
       "secret_binary" : "secret_binary",
       "secret_string" : "secret_string"
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
