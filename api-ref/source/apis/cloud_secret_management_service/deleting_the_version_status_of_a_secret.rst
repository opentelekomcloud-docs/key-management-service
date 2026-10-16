:original_name: kms_02_0228.html

.. _kms_02_0228:

Deleting the Version Status of a Secret
=======================================

Function
--------

This API is used to delete the status of a specified secret version.

Constraints
-----------

The **SYSCURRENT** and **SYSPREVIOUS** are preconfigured statuses and cannot be deleted.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

DELETE /v1/{project_id}/secrets/{secret_name}/stages/{stage_name}

.. table:: **Table 1** URI parameters

   =========== ========= ====== ================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ================================
   project_id  Yes       String Project ID.
   secret_name Yes       String Secret ID
   stage_name  Yes       String Name of a secret version status.
   =========== ========= ====== ================================

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

None

Example Request
---------------

Delete the **name** version status from secret **test**.

.. code-block:: text

   DELETE https://{csms_endpoint}/v1/{project_id}/secrets/test/stages/name

Example Response
----------------

None

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
