:original_name: kms_02_0014.html

.. _kms_02_0014:

Disabling a CMK
===============

Function
--------

This API allows you to disable a CMK. A disabled CMK cannot be used.

.. note::

   Only an enabled CMK can be disabled.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/disable-key

-  Parameter description

   .. table:: **Table 1** Parameters

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Requests
--------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | key_id          | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                 |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                      |
   +===========+===========+==================+==================================================================================================================================+
   | key_info  | Yes       | Array of objects | Information about keys. For details, see :ref:`Table 4 <kms_02_0014__en-us_topic_0112992300_t98d238e10953421e84a073707024c329>`. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0014__en-us_topic_0112992300_t98d238e10953421e84a073707024c329:

.. table:: **Table 4** **key_info** field description

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

Examples
--------

The following example describes how to disable a CMK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f"
      }

-  Example response

   .. code-block::

      {
          "key_info": {
              "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
              "key_state": "3"
          }
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

:ref:`Table 5 <kms_02_0014__en-us_topic_0112992300_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0014__en-us_topic_0112992300_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
