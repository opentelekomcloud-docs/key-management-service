:original_name: kms_02_0033.html

.. _kms_02_0033:

Encrypting Data
===============

Function
--------

This API enables you to encrypt data using a specified CMK.

.. note::

   By default, the performance threshold for encrypting data is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/encrypt-data

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
   | plain_text         | Yes             | String          | Plaintext data which is 1 to 4096 bytes in length and matches the regular expression **^.{1,4096}$**. After being converted into a byte array, it is still 1 to 4096 bytes in length.     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence           | No              | String          | A 36-byte serial number of a request message.                                                                                                                                             |
   |                    |                 |                 |                                                                                                                                                                                           |
   |                    |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                     |
   +--------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   =========== ========= ====== ================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ================================
   key_id      Yes       String CMK ID
   cipher_text Yes       String Ciphertext data in Base64 format
   =========== ========= ====== ================================

Example
-------

The following example describes how to use a CMK (ID: **0d0466b0-e727-4d9c-b35d-f84bb474a37f**) to encrypt data (plaintext: **12345678**).

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "plain_text": "12345678"
      }

-  Example response

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "cipher_text": "AgDoAG7EsEc2OHpQxz4gDFDH54CqwaelpTdEl+RFPjbKn5klPTvOywYIeZX60kPbFsYOpXJwkL32HUM50MY22Eb1fOSpZK7WJpYjx66EWOkJvO+Ey3r1dLdNAjrZrYzQlxRwNS05CaNKoX5rr3NoDnmv+UNobaiS25muLLiqOt6UrStaWow9AUyOHSzl+BrX2Vu0whv74djK+3COO6cXT2CBO6WajTJsOgYdxMfv24KWSKw0TqvHe8XDKASQGKdgfI74hzI1YWJlNjlmLWFlMTAtNDRjZC1iYzg3LTFiZGExZGUzYjdkNwAAAACdcfNpLXwDUPH3023MvZK8RPHe129k6VdNIi3zNb0eFQ=="
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

:ref:`Table 5 <kms_02_0033__en-us_topic_0112992287_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0033__en-us_topic_0112992287_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
