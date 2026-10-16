:original_name: kms_02_0224.html

.. _kms_02_0224:

Querying the Secret Version List
================================

Function
--------

This API is used to query the version list of a specific secret.

Constraints
-----------

The information returned via this API is the metadata of the secret version and does not contain the secret value.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

GET /v1/{project_id}/secrets/{secret_name}/versions

.. table:: **Table 1** URI parameters

   =========== ========= ====== ============
   Parameter   Mandatory Type   Description
   =========== ========= ====== ============
   project_id  Yes       String Project ID.
   secret_name Yes       String Secret name.
   =========== ========= ====== ============

.. table:: **Table 2** Query parameters

   +-----------+-----------+---------+-----------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                               |
   +===========+===========+=========+===========================================================+
   | marker    | No        | String  | Version number of the last item in the previous page.     |
   +-----------+-----------+---------+-----------------------------------------------------------+
   | limit     | No        | Integer | Number of items displayed per page. Default value: **50** |
   +-----------+-----------+---------+-----------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +-------------------+---------------------------------------------------------------------------------+------------------------+
   | Parameter         | Type                                                                            | Description            |
   +===================+=================================================================================+========================+
   | version_metadatas | Array of :ref:`VersionMetadata <kms_02_0224__response_versionmetadata>` objects | Version metadata       |
   +-------------------+---------------------------------------------------------------------------------+------------------------+
   | page_info         | :ref:`PageInfo <kms_02_0224__response_pageinfo>` object                         | Pagination information |
   +-------------------+---------------------------------------------------------------------------------+------------------------+

.. _kms_02_0224__response_versionmetadata:

.. table:: **Table 5** VersionMetadata

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================================================================+
   | id                    | String                | ID of a secret version. A secret cannot have duplicate version IDs.                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Secret creation time. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id            | String                | ID of the KMS CMK used to encrypt secret values.                                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_name           | String                | Secret name.                                                                                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_stages        | Array of strings      | Status list of a secret version. A status tag can be used for only one version of each secret. For example, if you add the status tag used by version A to version B, the tag will be moved from version A to version B. |
   |                       |                       |                                                                                                                                                                                                                          |
   |                       |                       | If the **version_stage** parameter is not specified, the status of the latest version will be **SYSCURRENT** by default.                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0224__response_pageinfo:

.. table:: **Table 6** PageInfo

   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                                |
   +=================+=========+============================================================================================================+
   | next_marker     | String  | Query address of the next page (secret name at the end of the current page and the start of the next page) |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | previous_marker | String  | Secret name at the start of the current page and the end of the last page                                  |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | current_count   | Integer | Number of records returned on the current page                                                             |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query all versions of secret **test**.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/secrets/test/versions

Example Response
----------------

.. code-block::

   {
     "version_metadatas" : [ {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
       "create_time" : 1581507580000,
       "secret_name" : "secret-name-demo",
       "version_stages" : [ "pending", "used" ]
     } ],
     "page_info" : {
       "next_marker" : "v10",
       "previous_marker" : "v1",
       "current_count" : 10
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
