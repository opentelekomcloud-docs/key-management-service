:original_name: kms_02_0015.html

.. _kms_02_0015:

Scheduling the Deletion of a CMK
================================

Function
--------

This API enables you to schedule the deletion of a CMK. A CMK can be scheduled to be deleted after 7 to 1,096 days.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/schedule-key-deletion

-  Parameter description

   .. table:: **Table 1** URI parameter

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Request Message
---------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                      |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | application/json                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                            |
   +=================+=================+=================+========================================================================================================================+
   | key_id          | Yes             | String          | 36-byte key ID that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**. |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | For example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f**                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | pending_days    | Yes             | String          | Number of days after which a CMK is scheduled to be deleted (The value ranges from **7** to **1,096**.)                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | A 36-byte serial number of a request message.                                                                          |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | key_id          | Yes             | String          | CMK ID                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | key_state       | Yes             | String          | CMK status:                                                |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  **2** indicates that the CMK is enabled.                |
   |                 |                 |                 | -  **3** indicates that the CMK is disabled.               |
   |                 |                 |                 | -  **4** indicates that the CMK is scheduled for deletion. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Example
-------

The following example describes how to schedule deletion of a CMK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "pending_days": "7"
      }

-  Example response

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "key_state": "4"
      }

   or

   .. code-block::

      {
          "error": {
              "error_code": "KMS.XXXX",
              "error_msg": "XXX"
          }
      }

Status Codes
------------

:ref:`Table 5 <kms_02_0015__en-us_topic_0112992297_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0015__en-us_topic_0112992297_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
