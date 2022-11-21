:original_name: kms_02_0021.html

.. _kms_02_0021:

Creating a Plaintext-Free DEK
=============================

Function
--------

This API allows you to create a plaintext-free DEK, that is, the returned result of this API includes only the ciphertext of the DEK.

.. note::

   By default, the performance threshold for creating plaintext-free DEKs is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/create-datakey-without-plaintext

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

   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                         |
   +====================+=================+=================+=====================================================================================================================================================================================+
   | key_id             | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**                                                          |
   |                    |                 |                 |                                                                                                                                                                                     |
   |                    |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                                                                                       |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encryption_context | No              | Object          | Key-value pairs with a maximum length of 8192 characters. This parameter is used to record resource context information, excluding sensitive information, to ensure data integrity. |
   |                    |                 |                 |                                                                                                                                                                                     |
   |                    |                 |                 | If this parameter is specified during encryption, it is also required for decryption.                                                                                               |
   |                    |                 |                 |                                                                                                                                                                                     |
   |                    |                 |                 | Example: {"Key1":"Value1","Key2":"Value2"}                                                                                                                                          |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datakey_length     | Yes             | String          | Number of bits of a key. The value is **512**.                                                                                                                                      |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence           | No              | String          | 36-byte serial number of a request message                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                     |
   |                    |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                       |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                       |
   +=============+===========+========+===================================================================================================+
   | key_id      | Yes       | String | CMK ID                                                                                            |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | cipher_text | Yes       | String | The ciphertext of a DEK is expressed in hexadecimal format, and two characters indicate one byte. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+

Examples
--------

The following example describes how to create a plaintext free DEK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "datakey_length": "512"
      }

-  Example response

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "cipher_text": "020098005CDC28E29EC3230AA42E8985FBABA095037D6474C64519C9B564AB28B15739C88E7E887500D1094973C2DC16353DB7ED3946C73339517AB1E983D521F9E9D700DC5D9C42F557EBF3F608E3CBBEE0BC68136EE7D2A49117E00332BAC4AE4ED805EB6068FA900C5A8019BFE2C2651BE3E130643034363662302D653732372D346439632D623335642D66383462623437346133376600000000F160727EBDB83400C21D80D713B49D3A2C37F24AE160E7BB3DAC025ADC0C45E3"
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

:ref:`Table 4 <kms_02_0021__en-us_topic_0112992350_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0021__en-us_topic_0112992350_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
