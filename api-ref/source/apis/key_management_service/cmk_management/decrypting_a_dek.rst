:original_name: kms_02_0023.html

.. _kms_02_0023:

Decrypting a DEK
================

Function
--------

This API enables you to decrypt a DEK using a specified CMK.

.. note::

   Data encryption results are used for decryption.

   By default, the performance threshold for decrypting DEKs is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/decrypt-datakey

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

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                               |
   +=======================+=================+=================+===========================================================================================================================================================================================+
   | key_id                | Yes             | String          | The value can be a key ID, alias (**key_alias**), or URN.                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                       |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                       |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 |    .. note::                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 |       The **alias_urn** generated during key alias creation is the URN.                                                                                                                   |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encryption_context    | No              | Object          | Key-value pairs with a maximum length of 8192 characters. This parameter is used to record resource context information, excluding sensitive information, to ensure data integrity.       |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 | If this parameter is specified during encryption, it is also required for decryption.                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 | Example: {"**Key1**":"**Value1**","**Key2**":"**Value2**"}                                                                                                                                |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cipher_text           | Yes             | String          | This parameter indicates the hexadecimal character string of the DEK ciphertext and the metadata. The value is the **cipher_text** value in the encryption result of a DEK.               |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datakey_cipher_length | Yes             | String          | Number of bytes of a key. The value is **64**.                                                                                                                                            |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence              | No              | String          | A 36-byte serial number of a request message.                                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                           |
   |                       |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                     |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   +----------------+-----------+--------+------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                    |
   +================+===========+========+================================================================================================+
   | data_key       | Yes       | String | Hexadecimal character string of the plaintext of a DEK                                         |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------+
   | datakey_length | Yes       | String | Number of bytes in the length of the plaintext of a DEK                                        |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------+
   | datakey_dgst   | Yes       | String | Hexadecimal character string corresponding to the SHA-256 hash value of the plaintext of a DEK |
   +----------------+-----------+--------+------------------------------------------------------------------------------------------------+

Example
-------

The following is an example about how to use a CMK (ID: **0d0466b0-e727-4d9c-b35d-f84bb474a37f**) to decrypt a DEK (ciphertext: **020098005273E14E6E8E95F5463BECDC27E80AF820B9FC086CB47861899149F67CF07DAFF2810B7D27BDF19AB7632488E0926A48DB2FC85BEA905119411B46244C5E6B8036C60A0B0B4842FFE6994518E89C19B1C1D688D9043BCD6053EA7BA0652642CE59F2543C80669139F4F71ABB9BD9A24330643034363662302D653732372D346439632D623335642D66383462623437346133376600000000D34457984F9730D57F228C210FD22CA6017913964B21D4ECE45D81092BB9112E**; length: **64** bits).

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "datakey_cipher_length": "64",
          "cipher_text": "020098005273E14E6E8E95F5463BECDC27E80AF820B9FC086CB47861899149F67CF07DAFF2810B7D27BDF19AB7632488E0926A48DB2FC85BEA905119411B46244C5E6B8036C60A0B0B4842FFE6994518E89C19B1C1D688D9043BCD6053EA7BA0652642CE59F2543C80669139F4F71ABB9BD9A24330643034363662302D653732372D346439632D623335642D66383462623437346133376600000000D34457984F9730D57F228C210FD22CA6017913964B21D4ECE45D81092BB9112E"
      }

-  Example response

   .. code-block::

      {
          "data_key": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
          "datakey_length": "64",
          "datakey_dgst": "F5A5FD42D16A20302798EF6ED309979B43003D2320D9F0E8EA9831A92759FB4B"
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

:ref:`Table 5 <kms_02_0023__en-us_topic_0112992306_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0023__en-us_topic_0112992306_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
