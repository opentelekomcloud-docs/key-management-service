:original_name: kms_02_0041.html

.. _kms_02_0041:

Querying the Rotation Status of a CMK
=====================================

Function
--------

This API enables you to query the rotation status of a CMK.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/get-key-rotation-status

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

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                      |
   +==============+===========+========+==================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling an IAM API. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | application/json                                                                                                                 |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                            |
   +=================+=================+=================+========================================================================================================================+
   | key_id          | Yes             | String          | 36-byte key ID that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**. |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | For example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f**                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | A 36-byte serial number of a request message.                                                                          |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                   |
   +======================+=================+=================+===============================================================================================================================+
   | key_rotation_enabled | Yes             | String          | Key rotation status. The default value is **false**, indicating that key rotation is disabled.                                |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | rotation_interval    | Yes             | Integer         | Rotation interval. The value is an integer ranging from **30** to **365**.                                                    |
   |                      |                 |                 |                                                                                                                               |
   |                      |                 |                 | Set the interval based on how often a CMK is used. If it is frequently used, set a short interval; otherwise, set a long one. |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | last_rotation_time   | Yes             | String          | Last key rotation time. The value is a timestamp expressed in the number of seconds since 00:00:00 UTC on January 1, 1970.    |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | number_of_rotations  | Yes             | String          | Number of key rotations                                                                                                       |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

Example
-------

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f"
      }

-  Example response

   .. code-block::

      {
          "key_rotation_enabled": true,
          "rotation_interval": 30,
          "last_rotation_time": "1501578672000",
          "number_of_rotations": 3
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

:ref:`Table 5 <kms_02_0041__en-us_topic_0112992305_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0041__en-us_topic_0112992305_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
