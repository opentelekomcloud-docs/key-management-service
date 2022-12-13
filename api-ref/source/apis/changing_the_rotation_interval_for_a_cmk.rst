:original_name: kms_02_0039.html

.. _kms_02_0039:

Changing the Rotation Interval for a CMK
========================================

Function
--------

This API enables you to change the rotation interval for a CMK.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/update-key-rotation-interval

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Requests
--------

.. table:: **Table 2** Request parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                   |
   +===================+=================+=================+===============================================================================================================================+
   | key_id            | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**    |
   |                   |                 |                 |                                                                                                                               |
   |                   |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                                 |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | rotation_interval | Yes             | Integer         | Rotation interval. The value is an integer ranging from **30** to **365**.                                                    |
   |                   |                 |                 |                                                                                                                               |
   |                   |                 |                 | Set the interval based on how often a CMK is used. If it is frequently used, set a short interval; otherwise, set a long one. |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | sequence          | No              | String          | 36-byte serial number of a request message                                                                                    |
   |                   |                 |                 |                                                                                                                               |
   |                   |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                 |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

None

Examples
--------

The following example describes how to change the rotation interval to **30** for a CMK (ID: **0d0466b0-e727-4d9c-b35d-f84bb474a37f**).

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "rotation_interval":30
      }

-  Example response

   .. code-block::

      {
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

:ref:`Table 3 <kms_02_0039__en-us_topic_0112992335_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0039__en-us_topic_0112992335_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 3** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
