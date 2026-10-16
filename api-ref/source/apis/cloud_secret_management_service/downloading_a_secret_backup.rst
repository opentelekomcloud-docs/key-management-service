:original_name: kms_02_0220.html

.. _kms_02_0220:

Downloading a Secret Backup
===========================

Function
--------

This API is used to download the backup file of a specified secret.

Constraints
-----------

This API returns a string indicating the secret backup file. The content is encrypted and cannot be read.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/secrets/{secret_name}/backup

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

Response Parameters
-------------------

.. table:: **Table 3** Response body parameter

   +-------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                                                                                                         |
   +=============+========+=====================================================================================================================================================================+
   | secret_blob | String | Backup file of a secret. The file contains information about all the versions of the secret. The backup file is encrypted and encoded, and cannot be directly read. |
   +-------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Download the backup data of secret **test**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/secrets/test/backup
   {
     "secret_blob":"this is secret_blob"
   }

Example Response
----------------

.. code-block::

   {
     "secret_blob":"this is secret_blob"
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
