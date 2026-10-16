:original_name: kms_02_0221.html

.. _kms_02_0221:

Creating a Scheduled Secret Deletion Task
=========================================

Function
--------

This API is used to create a scheduled task to delete a secret in 7 to 30 days.

Constraints
-----------

If a secret is in **Pending deletion** state, its metadata cannot be updated and its value cannot be viewed.

Debugging
---------

You can debug this API in . Automatic authentication is supported. API Explorer can automatically generate SDK code examples and provide the SDK code example debugging.

URI
---

POST /v1/{project_id}/secrets/{secret_name}/scheduled-deleted-tasks/create

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

.. table:: **Table 3** Request body parameter

   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                             |
   +=========================+=================+=================+=========================================================================================+
   | recovery_window_in_days | Yes             | Integer         | Create a scheduled secret deletion task and specify the waiting period before deletion. |
   |                         |                 |                 |                                                                                         |
   |                         |                 |                 | Constraints: The waiting period can be 7 to 30 days.                                    |
   |                         |                 |                 |                                                                                         |
   |                         |                 |                 | Default value: **30**                                                                   |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameter

   +-----------+-----------------------------------------------------+-------------+
   | Parameter | Type                                                | Description |
   +===========+=====================================================+=============+
   | secret    | :ref:`Secret <kms_02_0221__response_secret>` object | Secret      |
   +-----------+-----------------------------------------------------+-------------+

.. _kms_02_0221__response_secret:

.. table:: **Table 5** Secret parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================+
   | id                    | String                | Secret ID                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Secret name.                                                                                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                | Secret status. The value can be:                                                                                                             |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **ENABLED**                                                                                                                                  |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **DISABLED**                                                                                                                                 |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **PENDING_DELETE**                                                                                                                           |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **FROZEN**                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | kms_key_id            | String                | ID of the KMS CMK used to encrypt secret values                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description of a secret                                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Secret creation time. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Time when a secret was last updated. The timestamp indicates the total seconds past the start of the epoch date (January 1, 1970).           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_delete_time | Long                  | Time when a secret will be deleted as scheduled. The value is a timestamp which indicates how many seconds it has been since January 1, 1970 |
   |                       |                       |                                                                                                                                              |
   |                       |                       | If a secret is not in **Pending deletion** state, the value of this parameter is **null**.                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Create a scheduled deletion task for secret **test**. The secret will be deleted 15 days later.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/secrets/test/scheduled-deleted-tasks/create
   {
     "recovery_window_in_days" : 15
   }

Example Response
----------------

.. code-block::

   {
     "secret" : {
       "id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "name" : "test",
       "state" : "ENABLED",
       "kms_key_id" : "b168fe00ff56492495a7d22974df2d0b",
       "description" : "description",
       "create_time" : 1581507580000,
       "update_time" : 1581507580000,
       "scheduled_delete_time" : 1581507580000
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
