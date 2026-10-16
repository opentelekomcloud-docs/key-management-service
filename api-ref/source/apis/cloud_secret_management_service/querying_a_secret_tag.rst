:original_name: kms_02_0231.html

.. _kms_02_0231:

Querying a Secret Tag
=====================

Function
--------

-  This API is used to query a secret tag.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

GET /v1/{project_id}/csms/{secret_id}/tags

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

Response Parameters
-------------------

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                            | Description                                                                                                                                                                                            |
   +=======================+=================================================================+========================================================================================================================================================================================================+
   | tags                  | Array of :ref:`TagItem <kms_02_0231__response_tagitem>` objects | List of tags, including tag keys and tag values.                                                                                                                                                       |
   |                       |                                                                 |                                                                                                                                                                                                        |
   |                       |                                                                 | -  **key**: Tag key. A secret can contain up to 10 keys. This value cannot be left blank or repeated. The value of a **key** must be unique. The value of **key** contains a maximum of 36 characters. |
   |                       |                                                                 | -  **value**: Tag value. Each tag value can contain a maximum of 43 characters. A search result matches all the values.                                                                                |
   +-----------------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags              | Array of :ref:`TagItem <kms_02_0231__response_tagitem>` objects | List of tags, including tag keys and tag values.                                                                                                                                                       |
   |                       |                                                                 |                                                                                                                                                                                                        |
   |                       |                                                                 | -  **key**: Tag key. A secret can contain up to 10 keys. This value cannot be left blank or repeated. The value of a **key** must be unique. The value of **key** contains a maximum of 36 characters. |
   |                       |                                                                 | -  **value**: Tag value. Each tag value can contain a maximum of 43 characters. A search result matches all the values.                                                                                |
   +-----------------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0231__response_tagitem:

.. table:: **Table 4** TagItem

   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                                                                                        |
   +===========+========+====================================================================================================================================================================================================================================+
   | key       | String | Tag key. The value can contain at most 36 Unicode characters. The value of **key** cannot be empty. It cannot contain ASCII characters (0-31), asterisks (``*``), angle brackets (< and >), backslashes (\\), and equal signs (=). |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | String | Tag value. Each value can contain at most 43 Unicode characters and can be an empty string. It cannot contain ASCII characters (0-31), asterisks (``*``), angle brackets (< and >), backslashes (\\), and equal signs (=).         |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Obtain all tags of the secret whose ID is **fdb9c27f-4798-4eb9-b019-97578c5307b3**.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/csms/fdb9c27f-4798-4eb9-b019-97578c5307b3/tags

Example Response
----------------

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value2"
     } ],
     "sys_tags" : null
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
