:original_name: kms_02_0018.html

.. _kms_02_0018:

Querying the Information About a CMK
====================================

Function
--------

This API allows you to query the details about a CMK.

.. note::

   By default, the performance threshold for querying CMK details is 1000 TPS per customer. To apply for higher performance, submit a service ticket.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/describe-key

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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================+
   | key_id          | Yes             | String          | The value can be a key ID, alias (**key_alias**), or URN.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | -  Key ID: A 36-byte string that matches the **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** regular expression, for example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f** |
   |                 |                 |                 | -  Alias: An identifier of a key. The value starts with **alias/**, for example, **alias/4555**.                                                                                          |
   |                 |                 |                 | -  URN: Each alias automatically matches a unique URN, for example, **kms:eu-de-ring0:3ba44455500dd43127:alias:4555**.                                                                    |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 |    .. note::                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 |       The **alias_urn** generated during key alias creation is the URN.                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | A 36-byte serial number of a request message.                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                           |
   |                 |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameter

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                      |
   +===========+===========+==================+==================================================================================================================================+
   | key_info  | Yes       | Array of objects | Information about keys. For details, see :ref:`Table 5 <kms_02_0018__en-us_topic_0112992343_t98d238e10953421e84a073707024c329>`. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0018__en-us_topic_0112992343_t98d238e10953421e84a073707024c329:

.. table:: **Table 5** **key_info** field description

   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                                                                                      |
   +=========================+=================+=================+==================================================================================================================================================+
   | key_id                  | Yes             | String          | CMK ID                                                                                                                                           |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id               | Yes             | String          | User domain ID                                                                                                                                   |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_alias               | Yes             | String          | Alias of a CMK                                                                                                                                   |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | realm                   | Yes             | String          | Region where a CMK resides                                                                                                                       |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_description         | Yes             | String          | Description of a CMK                                                                                                                             |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_spec                | Yes             | String          | Key generation algorithm. Possible values are as follows:                                                                                        |
   |                         |                 |                 |                                                                                                                                                  |
   |                         |                 |                 | -  **AES_256**                                                                                                                                   |
   |                         |                 |                 | -  **RSA_2048**                                                                                                                                  |
   |                         |                 |                 | -  **RSA_3072**                                                                                                                                  |
   |                         |                 |                 | -  **RSA_4096**                                                                                                                                  |
   |                         |                 |                 | -  **EC_P256**                                                                                                                                   |
   |                         |                 |                 | -  **EC_P384**                                                                                                                                   |
   |                         |                 |                 | -  **HMAC_256**                                                                                                                                  |
   |                         |                 |                 | -  **HMAC_384**                                                                                                                                  |
   |                         |                 |                 | -  **HMAC_512**                                                                                                                                  |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_usage               | Yes             | String          | Key usage. Possible values are as follows:                                                                                                       |
   |                         |                 |                 |                                                                                                                                                  |
   |                         |                 |                 | -  **ENCRYPT_DECRYPT**                                                                                                                           |
   |                         |                 |                 | -  **SIGN_VERIFY**                                                                                                                               |
   |                         |                 |                 | -  **GENERATE_VERIFY_MAC**                                                                                                                       |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | creation_date           | Yes             | String          | Time when a key is created. The value is a timestamp expressed in the number of seconds since 00:00:00 UTC on January 1, 1970.                   |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_deletion_date | Yes             | String          | Time when a key will be deleted as scheduled. The value is a timestamp expressed in the number of seconds since 00:00:00 UTC on January 1, 1970. |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_state               | Yes             | String          | State of a CMK:                                                                                                                                  |
   |                         |                 |                 |                                                                                                                                                  |
   |                         |                 |                 | -  **1** indicates that the CMK is waiting to be activated.                                                                                      |
   |                         |                 |                 | -  **2** indicates that the CMK is enabled.                                                                                                      |
   |                         |                 |                 | -  **3** indicates that the CMK is disabled.                                                                                                     |
   |                         |                 |                 | -  **4** indicates that the CMK is scheduled for deletion.                                                                                       |
   |                         |                 |                 | -  **5** indicates that the CMK is waiting to be imported.                                                                                       |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_key_flag        | Yes             | String          | Identification of a Master Key. The value **1** indicates a Default Master Key, and the value **0** indicates a CMK.                             |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_type                | Yes             | String          | Type of a CMK                                                                                                                                    |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | expiration_time         | Yes             | String          | Expiration time of the key material. It is expressed in the form of a time stamp, the total number of seconds since January 1, 1970.             |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | origin                  | Yes             | String          | Origin of a CMK. The default value is **kms**. The following values are enumerated:                                                              |
   |                         |                 |                 |                                                                                                                                                  |
   |                         |                 |                 | -  **kms** indicates that the CMK material is generated by KMS.                                                                                  |
   |                         |                 |                 | -  **external** indicates that the CMK material is imported.                                                                                     |
   +-------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Example
-------

The following example describes how to query the information of a CMK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

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
              "domain_id": "b168fe00ff56492495a7d22974df2d0b",
              "key_alias": "kms_test",
              "realm": "aaa",
              "key_description": "",
              "creation_date": "1472442386000",
              "scheduled_deletion_date": "",
              "key_state": "2",
              "default_key_flag": "0",
              "key_type": "1",
              "expiration_time":"1501578672000",
              "origin":"kms"
              ,
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

:ref:`Table 6 <kms_02_0018__en-us_topic_0112992343_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0018__en-us_topic_0112992343_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 6** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
