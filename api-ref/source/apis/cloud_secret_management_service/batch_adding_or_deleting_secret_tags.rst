:original_name: kms_02_0230.html

.. _kms_02_0230:

Batch Adding or Deleting Secret Tags
====================================

Function
--------

-  This API is used to add or delete secret tags in batches.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/csms/{secret_id}/tags/action

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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                           | Description                                                                               |
   +===========+===========+================================================================+===========================================================================================+
   | tags      | No        | Array of :ref:`TagItem <kms_02_0230__request_tagitem>` objects | List of tags, including tag keys and tag values.                                          |
   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | action    | No        | String                                                         | Operation. Its value can be **create** or **delete**.                                     |
   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | sequence  | No        | String                                                         | 36-byte serial number of a request message. Example: 919c82d4-8046-4722-9094-35c3c6524cff |
   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------+

.. _kms_02_0230__request_tagitem:

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

Batch add tags for the secret whose ID is **fdb9c27f-4798-4eb9-b019-97578c5307b3**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/csms/fdb9c27f-4798-4eb9-b019-97578c5307b3/tags/action
   {
     "action" : "create",
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value2"
     } ]
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
