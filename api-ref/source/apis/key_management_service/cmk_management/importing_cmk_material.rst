:original_name: kms_02_0036.html

.. _kms_02_0036:

Importing CMK Material
======================

Function
--------

This API allows you to import CMK material.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/import-key-material

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

   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                                                                                                                    |
   +========================+=================+=================+================================================================================================================================================================================================================+
   | key_id                 | Yes             | String          | 36-byte key ID that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**.                                                                                         |
   |                        |                 |                 |                                                                                                                                                                                                                |
   |                        |                 |                 | For example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f**                                                                                                                                                          |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | import_token           | Yes             | String          | CMK import token in Base64 format that matches the regular expression **^[0-9a-zA-Z+/=]{200,6144}$**                                                                                                           |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encrypted_key_material | Yes             | String          | Encrypted CMK material in Base64 format that matches the regular expression ^[0-9a-zA-Z+/=]{344,360}$                                                                                                          |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expiration_time        | No              | String          | Expiration time of the key material. The value is a timestamp expressed in the number of seconds since 00:00:00 UTC on January 1, 1970. KMS will delete the key material within 24 hours after the expiration. |
   |                        |                 |                 |                                                                                                                                                                                                                |
   |                        |                 |                 | Example: 1550291833                                                                                                                                                                                            |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence               | No              | String          | A 36-byte serial number of a request message.                                                                                                                                                                  |
   |                        |                 |                 |                                                                                                                                                                                                                |
   |                        |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                                          |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

None

Example
-------

The following example describes how to import the CMK material and the import-token to the CMK whose ID is **bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e**, and set the expiration time of the CMK material to **1521578672**.

-  Example request

   .. code-block::

      {
          "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
          "import_token":"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",
          "encrypted_key_material":"K+ixymtl90e+B5Rdan89KjDslBIoOexrIwzkYHGz3odS7FDXDkogqbWwwJg5wQ6zjUbEvsR/+Fi+A0SSkhhqtijivOKHu4Z86RWjOCBdrr9es+ZhJ0zYBNMN+7Rf2fd9vxbb873Q7VBkJRyH1hi3Wh+kLmDW4rpWZm4+YGCtWylz7ZKbV1KBlhSNLDtZzT4nxUra0p7Die4HgUUxSjZTOr/0s71yF6o2eysreIzIl+GbpCft0WpRsxN2Ng++ntgOcwOf2zOC9o/tjraxeAvgGw+Dwt4cjF4znnFf0LPQ2YvpNUo248LjAGxdFvzUABNzfYSj3RZ0K3wQCNAcXU3HYw==",
          "expiration_time":1521578672
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

:ref:`Table 4 <kms_02_0036__en-us_topic_0112992337_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0036__en-us_topic_0112992337_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
