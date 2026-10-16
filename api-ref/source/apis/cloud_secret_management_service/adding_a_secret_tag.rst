:original_name: kms_02_0232.html

.. _kms_02_0232:

Adding a Secret Tag
===================

Function
--------

-  This API is used to add a secret tag.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/csms/{secret_id}/tags

.. table:: **Table 1** URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   secret_id  Yes       String Secret ID.
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

.. table:: **Table 3** Request body parameter

   +-----------+-----------+------------------------------------------------------+-------------+
   | Parameter | Mandatory | Type                                                 | Description |
   +===========+===========+======================================================+=============+
   | tag       | No        | :ref:`TagItem <kms_02_0232__request_tagitem>` object | ``-``       |
   +-----------+-----------+------------------------------------------------------+-------------+

.. _kms_02_0232__request_tagitem:

.. table:: **Table 4** TagItem

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                        |
   +===========+===========+========+====================================================================================================================================================================================================================================+
   | key       | No        | String | Tag key. The value can contain at most 36 Unicode characters. The value of **key** cannot be empty. It cannot contain ASCII characters (0-31), asterisks (``*``), angle brackets (< and >), backslashes (\\), and equal signs (=). |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | No        | String | Tag value. Each value can contain at most 43 Unicode characters and can be an empty string. It cannot contain ASCII characters (0-31), asterisks (``*``), angle brackets (< and >), backslashes (\\), and equal signs (=).         |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

Add a tag to the secret whose ID is **fdb9c27f-4798-4eb9-b019-97578c5307b3**. The tag key is **DEV** and the tag value is **DEV1**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/csms/fdb9c27f-4798-4eb9-b019-97578c5307b3/tags
   {
     "tag" : {
       "key" : "DEV",
       "value" : "DEV1"
     }
   }

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
