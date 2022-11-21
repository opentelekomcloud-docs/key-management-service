:original_name: kms_02_0022.html

.. _kms_02_0022:

Encrypting a DEK
================

Function
--------

This API enables you to encrypt a DEK using a specified CMK.

.. note::

   By default, the performance threshold for encrypting DEKs is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/encrypt-datakey

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

   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                                                                         |
   +======================+=================+=================+=====================================================================================================================================================================================+
   | key_id               | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**                                                          |
   |                      |                 |                 |                                                                                                                                                                                     |
   |                      |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                                                                                       |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encryption_context   | No              | Object          | Key-value pairs with a maximum length of 8192 characters. This parameter is used to record resource context information, excluding sensitive information, to ensure data integrity. |
   |                      |                 |                 |                                                                                                                                                                                     |
   |                      |                 |                 | If this parameter is specified during encryption, it is also required for decryption.                                                                                               |
   |                      |                 |                 |                                                                                                                                                                                     |
   |                      |                 |                 | Example: {"Key1":"Value1","Key2":"Value2"}                                                                                                                                          |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | plain_text           | Yes             | String          | Hexadecimal character string concatenated from plaintext of a DEK and the plaintext digest (32-byte character string generated using SHA256)                                        |
   |                      |                 |                 |                                                                                                                                                                                     |
   |                      |                 |                 | For details, see :ref:`Examples <kms_02_0022__en-us_topic_0112992344_section144011443913>`.                                                                                         |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datakey_plain_length | Yes             | String          | Number of bytes of a DEK in plaintext. The value is **64**.                                                                                                                         |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence             | No              | String          | 36-byte serial number of a request message                                                                                                                                          |
   |                      |                 |                 |                                                                                                                                                                                     |
   |                      |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                       |
   +----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                       |
   +================+===========+========+===================================================================================================+
   | key_id         | Yes       | String | CMK ID                                                                                            |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | cipher_text    | Yes       | String | The ciphertext of a DEK is expressed in hexadecimal format, and two characters indicate one byte. |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | datakey_length | Yes       | String | Number of bytes in the length of a DEK                                                            |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------+

.. _kms_02_0022__en-us_topic_0112992344_section144011443913:

Examples
--------

In the following example, the 512-bit plaintext DEK (**7549d9aea901767bf3c0b3e14b10722eaf6f59053bbd82045d04e075e809a0fe6ccab48f8e5efe74e4b18ff0512525e527b10331100f357bf42125d8d5ced94f**) generated from the customer master key whose key ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f** can be obtained through the API in :ref:`Creating a DEK <kms_02_0020>`.

The digest of the plaintext DEK is **fbc8ac72b0785ca7fe33eb6776ce3990b11e32b299d9c0a9ee0305fb9540f797**. The method for calculating the digest is as follows:

.. code-block::

   //Digest calculation
   public static byte[] sha256(byte[] cmkData) {
       byte[] digest = new byte[0];
      try {
          MessageDigest md = MessageDigest.getInstance("SHA-256");
            md.update(cmkData);
           digest = md.digest();
        } catch (Exception e) {
           System.out.println("calculate digest failure, exception is " + e.toString());
       }
        return digest;
   }
   //Convert the obtained digest into a hexadecimal character string.
   public static String bytesToHexString(byte[] digest) {
           ...
   }

The value of **plain_text** (a hexadecimal character string concatenated from plaintext of the DEK and the plaintext digest) is **7549d9aea901767bf3c0b3e14b10722eaf6f59053bbd82045d04e075e809a0fe6ccab48f8e5efe74e4b18ff0512525e527b10331100f357bf42125d8d5ced94f fbc8ac72b0785ca7fe33eb6776ce3990b11e32b299d9c0a9ee0305fb9540f797**.

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "plain_text": "7549d9aea901767bf3c0b3e14b10722eaf6f59053bbd82045d04e075e809a0fe6ccab48f8e5efe74e4b18ff0512525e527b10331100f357bf42125d8d5ced94f fbc8ac72b0785ca7fe33eb6776ce3990b11e32b299d9c0a9ee0305fb9540f797",
          "datakey_plain_length": "64"
      }

-  Example response

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "cipher_text": "020098005273E14E6E8E95F5463BECDC27E80AF820B9FC086CB47861899149F67CF07DAFF2810B7D27BDF19AB7632488E0926A48DB2FC85BEA905119411B46244C5E6B8036C60A0B0B4842FFE6994518E89C19B1C1D688D9043BCD6053EA7BA0652642CE59F2543C80669139F4F71ABB9BD9A24330643034363662302D653732372D346439632D623335642D66383462623437346133376600000000D34457984F9730D57F228C210FD22CA6017913964B21D4ECE45D81092BB9112E",
          "datakey_length": "64"
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

:ref:`Table 4 <kms_02_0022__en-us_topic_0112992344_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0022__en-us_topic_0112992344_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
