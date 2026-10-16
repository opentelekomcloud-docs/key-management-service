:original_name: kms_02_0226.html

.. _kms_02_0226:

Updating the Version Status of a Secret
=======================================

Function
--------

This API is used to update the version status of a secret.

Constraints
-----------

-  A status tag can be used for only one version of each secret. For example, if you add the status tag used by version A to version B, the tag will be moved from version A to version B. Versions without any statuses are regarded as deprecated versions and can be automatically deleted by CSMS.
-  A secret can have up to 12 version statuses. A status can be used for only one version. **SYSCURRENT** and **SYSPREVIOUS** are the preconfigured secret statuses of a service.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

PUT /v1/{project_id}/secrets/{secret_name}/stages/{stage_name}

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                         |
   +=============+===========+========+=====================================================================================================+
   | project_id  | Yes       | String | Project ID.                                                                                         |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | secret_name | Yes       | String | Secret name.                                                                                        |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | stage_name  | Yes       | String | Name of a secret version status. It must match the regular expression **'^[a-zA-Z0-9._-]{1,64}$'**. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameter

   ========== ========= ====== =================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =================
   version_id Yes       String Secret version ID
   ========== ========= ====== =================

Response Parameters
-------------------

.. table:: **Table 4** Response body parameter

   +-----------+---------------------------------------------------+---------------+
   | Parameter | Type                                              | Description   |
   +===========+===================================================+===============+
   | stage     | :ref:`Stage <kms_02_0226__response_stage>` object | Secret status |
   +-----------+---------------------------------------------------+---------------+

.. _kms_02_0226__response_stage:

.. table:: **Table 5** Stage

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                    |
   +=======================+=======================+================================================================================================================================+
   | name                  | String                | Name of a secret version status.                                                                                               |
   |                       |                       |                                                                                                                                |
   |                       |                       | Constraint: 1 to 64 characters long                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Secret version update timestamp. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | secret_name           | String                | Secret name.                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | version_id            | String                | Secret version ID                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Update the version status of the **test** secret to **name**.

.. code-block:: text

   PUT https://{csms_endpoint}/v1/{project_id}/secrets/test/stages/name
   {
     "version_id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e"
   }

Example Response
----------------

.. code-block::

   {
     "stage" : {
       "name" : "name",
       "version_id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "update_time" : 1581507580000,
       "secret_name" : "secret-name-demo"
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
