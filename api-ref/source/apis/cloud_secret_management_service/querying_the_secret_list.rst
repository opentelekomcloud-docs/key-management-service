:original_name: kms_02_0215.html

.. _kms_02_0215:

Querying the Secret List
========================

Function
--------

This API is used to query all the secrets created by the current user in the current project.

Constraints
-----------

The information returned via this API is the metadata of the secret and does not contain the secret value.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

GET /v1/{project_id}/secrets

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                               |
   +=================+=================+=================+===========================================================================================================================+
   | limit           | No              | String          | Number of results returned on each page                                                                                   |
   |                 |                 |                 |                                                                                                                           |
   |                 |                 |                 | Default value: 50                                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Starting secret name of pagination query. If the parameter is left blank, only the secrets on the first page are queried. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------+------------------------+
   | Parameter | Type                                                          | Description            |
   +===========+===============================================================+========================+
   | secrets   | Array of :ref:`Secret <kms_02_0215__response_secret>` objects | Secret list            |
   +-----------+---------------------------------------------------------------+------------------------+
   | page_info | :ref:`PageInfo <kms_02_0215__response_pageinfo>` object       | Pagination information |
   +-----------+---------------------------------------------------------------+------------------------+

.. _kms_02_0215__response_secret:

.. table:: **Table 5** Secret parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================+
   | id                    | String                | Secret ID                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Secret name.                                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                | Secret status. Its value can be:                                                                                                               |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **ENABLED**                                                                                                                                    |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **DISABLED**                                                                                                                                   |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **PENDING_DELETE**                                                                                                                             |
   |                       |                       |                                                                                                                                                |
   |                       |                       | **FROZEN**                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id            | String                | ID of the KMS CMK used to encrypt secret values                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description of a secret                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Secret creation time. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Time when a secret was last updated. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_delete_time | Long                  | Time when a secret will be deleted as scheduled. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970). |
   |                       |                       |                                                                                                                                                |
   |                       |                       | If a secret is not in **Pending deletion** state, the value of this parameter is **null**.                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0215__response_pageinfo:

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

Obtain all the secrets created in the current project.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/secrets

Example Response
----------------

.. code-block::

   {
     "secrets" : [ {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "name" : "secret-name-test",
       "state" : "ENABLED",
       "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
       "description" : "description",
       "create_time" : 1581507580000,
       "update_time" : 1581507580000,
       "scheduled_delete_time" : 1581507580000
     } ],
     "page_info" : {
       "next_marker" : "secret-name-test",
       "previous_marker" : "secret-name-test",
       "current_count" : 1
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
