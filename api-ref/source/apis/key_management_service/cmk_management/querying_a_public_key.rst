:original_name: ShowPublicKey.html

.. _ShowPublicKey:

Querying a Public Key
=====================

Function
--------

-  This API is used to query the public key information of a specified asymmetric key.

Constraints
-----------

This API cannot be used to obtain the public key of a symmetric key.

URI
---

POST /v1.0/{project_id}/kms/get-publickey

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                |
   |                 |                 |                 |                                                                                                                                            |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is a token. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Application/JSON                                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================+
   | key_id          | Yes             | String          | ID of the key to be enabled. The value can be the key ID, alias (**key_alias**), or URN.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                 |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                 |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | A 36-byte serial number of a request message.                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   key_id     String Key ID
   public_key String Public key information
   ========== ====== ======================

Example Request
---------------

Query the information about the public key whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

.. code-block::

   {
     "key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f"
   }

Example Response
----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "key_id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
     "public_key" : "-----BEGIN PUBLIC KEY-----\r\nMIICCgKCAgEA3RQAXXwya9k4zV1/Q3AFr37GO8JgFobDKZioAklLQdgElHZ/uxmP\r\n4bveNHpY6OI0Okk/1Ov8oJf+9W10VqVxbzihWa5n/RMN0720DzLV7KuH4YylCGDb\r\n3JH/+bMbhF2qRArrrKod0kR9rYHrdPkI7O5fYQQprZ3kWnPgrhDoDFC8ja+OelOg\r\nn4MMOGGYA/DAOb0XyxPnGl26PnUtvvF7aZbMW5x/Yq2yAVFE1cjqLaH7/j1C8KYE\r\naOSYtl2nOif28WoweFavXpgVsb/iICTfqgC91BtCSFC5pT8vqZCimfoHmJCAkZa5\r\nZ8QIqkOOf9F6iMqqIz7pGKgQSUmoKKY9j6DK3OwXDOB5gKu0vyuz+gW3b4SZn+Xa\r\nKkEN8ZpXsdQdEGpe4SwIzSVyUGYNBOCLrsydBcPR7jWgQ6gs56IJrV2pdAtmBwKd\r\n6l33z1tQ7+/h3IrZxXuuej/fRRUMlbVcmhTS2l6vle7HXgZj/dWzPsLLg9MGHu0+\r\no9PRr+brxTbrf5e2Zdr1ad35X/b86gx7Grg1sYPkly2aEI4fsnDGPgFrudG+Hzx/\r\nABHejYfJEI6P0SXCzB/oDMkjw6XKhTSojMzuncAP/AM+0LVYQxQe750qkb3hjBT0\r\nq/HBl/4zMXA03tMb9QySnLK63uo64JMJiBsEe7wPLhHB3VzBZk9SvvECAwEAAQ==\r\n-----END PUBLIC KEY-----\r\n"
   }

Status Codes
------------

=========== ====== ==================
Status Code Status Description
=========== ====== ==================
200         OK     Request succeeded.
=========== ====== ==================
