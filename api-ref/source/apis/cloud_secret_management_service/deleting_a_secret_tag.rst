:original_name: kms_02_0233.html

.. _kms_02_0233:

Deleting a Secret Tag
=====================

Function
--------

-  This API is used to delete a secret tag.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

DELETE /v1/{project_id}/csms/{secret_id}/tags/{key}

.. table:: **Table 1** URI parameters

   ========== ========= ====== ==================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==================
   project_id Yes       String Project ID.
   secret_id  Yes       String Secret ID.
   key        Yes       String Value of a tag key
   ========== ========= ====== ==================

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

Delete the tag whose key is **DEV** from the secret whose ID is **fdb9c27f-4798-4eb9-b019-97578c5307b3**.

.. code-block:: text

   DELETE https://{csms_endpoint}/v1/{project_id}/csms/fdb9c27f-4798-4eb9-b019-97578c5307b3/tags/DEV

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
