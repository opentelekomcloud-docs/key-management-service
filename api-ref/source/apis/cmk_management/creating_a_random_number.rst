:original_name: kms_02_0019.html

.. _kms_02_0019:

Creating a Random Number
========================

Function
--------

This API generates a 512-bit random number.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/gen-random

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

   +--------------------+-----------------+-----------------+----------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                              |
   +====================+=================+=================+==========================================================+
   | random_data_length | Yes             | String          | Number of bits of a random number. The value is **512**. |
   +--------------------+-----------------+-----------------+----------------------------------------------------------+
   | sequence           | No              | String          | 36-byte serial number of a request message               |
   |                    |                 |                 |                                                          |
   |                    |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff            |
   +--------------------+-----------------+-----------------+----------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                 |
   +=============+===========+========+=============================================================================================================================================================================================+
   | random_data | Yes       | String | Random numbers are expressed in hexadecimal format. Two characters indicate one byte. Length of a random number must be consistent with the **random_data_length** value entered by a user. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Examples
--------

The following example describes how to create a random number with the length of **512** bits.

-  Example request

   .. code-block::

      {
          "random_data_length": "512"
      }

-  Example response

   .. code-block::

      {
          "random_data": "5791C223E87124AB9FC29B5A8AC60BE4B98D168F47A58BB2A88833E40D6ED32D57E2AAB5410492EB25096873F9CE3D45E0D22F820A5AB4EEADC33A1A6AE780F1"
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

:ref:`Table 4 <kms_02_0019__en-us_topic_0112992308_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0019__en-us_topic_0112992308_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
