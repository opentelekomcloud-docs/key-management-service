:original_name: kms_02_0012.html

.. _kms_02_0012:

Creating a CMK
==============

Function
--------

This API is used to create customer master keys (CMKs) used to encrypt data encryption keys (DEKs).

.. note::

   Default Master Keys are created by services integrated with KMS. Names of Default Master Keys end with **/default**. Therefore, in naming your CMKs, do not choose those ending with **/default**.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/create-key

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

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================================================================+
   | key_alias       | Yes             | String          | Alias of a non-default master key (The alias's length ranges from 1 to 255 characters and matches the regular expression **^[a-zA-Z0-9:/_-]{1,255}$**. In addition, it must be different from the alias of a Default Master Key created by the system.) |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_spec        | No              | String          | Key generation algorithm. The default value is **AES_256**. Its value can be:                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  AES_256                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  RSA_2048                                                                                                                                                                                                                                             |
   |                 |                 |                 | -  RSA_3072                                                                                                                                                                                                                                             |
   |                 |                 |                 | -  RSA_4096                                                                                                                                                                                                                                             |
   |                 |                 |                 | -  EC_P256                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  EC_P384                                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_usage       | No              | String          | Key usage. The default value is **ENCRYPT_DECRYPT** for a symmetric key and **SIGN_VERIFY** for an asymmetric key. Its value can be:                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  For AES_256 symmetric keys, the default value is **ENCRYPT_DECRYPT**.                                                                                                                                                                                |
   |                 |                 |                 | -  For RSA asymmetric keys, select **ENCRYPT_DECRYPT** or **SIGN_VERIFY**. The default value is **SIGN_VERIFY**.                                                                                                                                        |
   |                 |                 |                 | -  For ECC asymmetric keys, the default value is **SIGN_VERIFY**.                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_description | No              | String          | CMK description (The value ranges from 0 to 255 characters.)                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | origin          | No              | String          | Origin of a CMK. The default value is **kms**. The following values are enumerated:                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  **kms** indicates that the CMK material is generated by KMS.                                                                                                                                                                                         |
   |                 |                 |                 | -  **external** indicates that the CMK material is imported.                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                         |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                      |
   +===========+===========+==================+==================================================================================================================================+
   | key_info  | Yes       | Array of objects | Information about keys. For details, see :ref:`Table 4 <kms_02_0012__en-us_topic_0112992294_t98d238e10953421e84a073707024c329>`. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0012__en-us_topic_0112992294_t98d238e10953421e84a073707024c329:

.. table:: **Table 4** **key_info** field description

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   key_id    Yes       String CMK ID
   domain_id Yes       String User domain ID
   ========= ========= ====== ==============

Examples
--------

The following example describes how to create a CMK with an alias of **test**.

-  Example request

   .. code-block::

      {
          "key_alias": "test"
      }

-  Example response

   .. code-block::

      {
          "key_info": {
              "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
              "domain_id": "b168fe00ff56492495a7d22974df2d0b"
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

:ref:`Table 5 <kms_02_0012__en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0012__en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
