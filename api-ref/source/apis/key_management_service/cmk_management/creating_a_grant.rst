:original_name: kms_02_0028.html

.. _kms_02_0028:

Creating a Grant
================

Function
--------

This API enables you to create a grant to grant permissions on a CMK to a user so that the user can perform operations on the CMK.

.. note::

   A Default Master Key (the alias suffix of which is **/default**) does not allow permission granting.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/create-grant

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

   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type             | Description                                                                                                                                                      |
   +========================+=================+==================+==================================================================================================================================================================+
   | key_id                 | Yes             | String           | 36-byte key ID that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**.                                           |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | For example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f**                                                                                                            |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | grantee_principal      | Yes             | String           | Indicates the ID of the authorized user. The value is between 1 to 64 bytes and meets the regular expression **"^[a-zA-Z0-9]{1,64}$"**.                          |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | Example: 0d0466b00d0466b00d0466b00d0466b0                                                                                                                        |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | operations             | Yes             | Array of strings | Permissions that can be granted                                                                                                                                  |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | Values: **create-datakey**, **create-datakey-without-plaintext**, **encrypt-datakey**, **decrypt-datakey**, **describe-key**, **create-grant**, **retire-grant** |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | **create-grant** cannot be the only value.                                                                                                                       |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                   | No              | String           | Name of a grant which can be 1 to 255 characters in length and matches the regular expression **^[a-zA-Z0-9:/_-]{1,255}$**                                       |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retiring_principal     | No              | String           | Indicates the ID of the retiring user. The value is between 1 to 64 bytes and meets the regular expression **"^[a-zA-Z0-9]{1,64}$"**.                            |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | Example: 0d0466b00d0466b00d0466b00d0466b0                                                                                                                        |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | grantee_principal_type | No              | String           | Authorization type                                                                                                                                               |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | The value can be **user** or **domain**. The default value is **user**.                                                                                          |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence               | No              | String           | A 36-byte serial number of a request message.                                                                                                                    |
   |                        |                 |                  |                                                                                                                                                                  |
   |                        |                 |                  | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                            |
   +------------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameter

   ========= ========= ====== =====================
   Parameter Mandatory Type   Description
   ========= ========= ====== =====================
   grant_id  Yes       String 64-byte ID of a grant
   ========= ========= ====== =====================

Example
-------

The following example shows how to grant the **describe-key**, **create-datakey**, and **encrypt-datakey** permissions of CMK (ID: **bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e**) to the user whose ID is **13gg44z4g2sglzk0egw0u726zoyzvrs8**. The authorization name is **my_grant**, and the user (ID: **13gg44z4g2sglzk0egw0u726zoyzvrs8**) can retire a grant.

-  Example request

   .. code-block::

      {
          "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
          "operations": [
             "describe-key",
             "create-datakey",
             "encrypt-datakey"
           ],
           "grantee_principal":"13gg44z4g2sglzk0egw0u726zoyzvrs8",
           "name":"my_grant",
           "retiring_principal":"13gg44z4g2sglzk0egw0u726zoyzvrs8"
      }

-  Example response

   .. code-block::

      {
          "grant_id": "7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d"
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

:ref:`Table 5 <kms_02_0028__en-us_topic_0112992333_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0028__en-us_topic_0112992333_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
