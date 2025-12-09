:original_name: kms_02_0020.html

.. _kms_02_0020:

Creating a DEK
==============

Function
--------

This API allows you to create a DEK. A returned result includes the plaintext and the ciphertext of a DEK.

.. note::

   By default, the performance threshold for creating DEKs is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/create-datakey

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

   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                               |
   +====================+=================+=================+===========================================================================================================================================================================================+
   | key_id             | Yes             | String          | The value can be a key ID, alias (**key_alias**), or URN.                                                                                                                                 |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                    |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                    |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 |    .. note::                                                                                                                                                                              |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 |       The **alias_urn** generated during key alias creation is the URN.                                                                                                                   |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encryption_context | No              | Object          | Key-value pairs with a maximum length of 8192 characters. This parameter is used to record resource context information, excluding sensitive information, to ensure data integrity.       |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 | If this parameter is specified during encryption, it is also required for decryption.                                                                                                     |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 | Example: {"**Key1**":"**Value1**","**Key2**":"**Value2**"}                                                                                                                                |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datakey_length     | Yes             | String          | Number of bits of a key. The value is **512**.                                                                                                                                            |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence           | No              | String          | A 36-byte serial number of a request message.                                                                                                                                             |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                       |
   +=============+===========+========+===================================================================================================+
   | key_id      | Yes       | String | CMK ID                                                                                            |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | plain_text  | Yes       | String | The plaintext of a DEK is expressed in hexadecimal format, and two characters indicate one byte.  |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | cipher_text | Yes       | String | The ciphertext of a DEK is expressed in hexadecimal format, and two characters indicate one byte. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+

Example
-------

The following example describes how to create a DEK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f** and length is **512** bits.

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
          "plain_text": "8151014275E426C72EE7D44267EF11590DCE0089E19863BA8CC832187B156A72A5A17F17B5EF0D525872C59ECEB72948AF85E18427F8BE0D46545C979306C08D",
          "cipher_text": "020098009EEAFCE122CAA5927D2E020086F9548BA1675FDB022E4ECC01B96F2189CF4B85E78357E73E1CEB518DAF7A4960E7C7DE8885ED3FB2F1471ABF400119CC1B20BD3C4A9B80AF590EFD0AEDABFDBB0E2B689DA7B6C9E7D3C5645FCD9274802586BE63779471F9156F2CDF07CD8412FFBE9230643034363662302D653732372D346439632D623335642D6638346262343734613337660000000045B05321483BD9F9561865EE7DFE9BE267A42EB104E98C16589CE46940B18E52"
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

:ref:`Table 5 <kms_02_0020__en-us_topic_0112992330_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0020__en-us_topic_0112992330_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
