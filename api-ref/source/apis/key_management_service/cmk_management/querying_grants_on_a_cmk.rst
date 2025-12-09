:original_name: kms_02_0031.html

.. _kms_02_0031:

Querying Grants on a CMK
========================

Function
--------

This API enables you to query grants on a CMK.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/list-grants

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

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================================================================+
   | key_id          | Yes             | String          | 36-byte key ID that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**.                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For example, **0d0466b0-e727-4d9c-b35d-f84bb474a37f**                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String          | This parameter specifies the number of entries returned. If the specified number is smaller than the actual number of existing entries, **true** will be returned for the response parameter **truncated**, indicating that the query results will be displayed in separate pages. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | The value is within the range of the maximum number of grants, for example, **100**.                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | This parameter marks the starting location in a pagination query.                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | If the **truncated** value is **true**, you can send consecutive requests to obtain more record entries. The **marker** value must be set to the **next_marker** value in the response, for example, **10**.                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | A 36-byte serial number of a request message.                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For example, **919c82d4-8046-4722-9094-35c3c6524cff**                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 4** Response parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                            |
   +=================+=================+==================+========================================================================================================+
   | grants          | Yes             | Array of objects | Grant list. For details, see :ref:`Table 5 <kms_02_0031__en-us_topic_0112992310_table17099798154440>`. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------+
   | next_marker     | Yes             | String           | This parameter indicates the **marker** value required for obtaining the next page of query results.   |
   |                 |                 |                  |                                                                                                        |
   |                 |                 |                  | If the **truncated** value is **false**, the **next_marker** parameter is left blank.                  |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------+
   | truncated       | Yes             | String           | This parameter indicates whether there are more results displayed in another page.                     |
   |                 |                 |                  |                                                                                                        |
   |                 |                 |                  | -  If the value is **true**, there are more results.                                                   |
   |                 |                 |                  | -  If the value is **false**, the current page is the last page.                                       |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------+
   | total           | Yes             | Integer          | This parameter indicates the total number of grants.                                                   |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------+

.. _kms_02_0031__en-us_topic_0112992310_table17099798154440:

.. table:: **Table 5** **grants** field description

   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type             | Description                                                                                                                                                                                       |
   +====================+=================+==================+===================================================================================================================================================================================================+
   | key_id             | Yes             | String           | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**                                                                        |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                                                                                                     |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | grant_id           | Yes             | String           | 64-byte ID of a grant that meets the regular expression **^[A-Fa-f0-9]{64}$**                                                                                                                     |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d                                                                                                                         |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | grantee_principal  | Yes             | String           | Indicates the ID of the authorized user. The value is between 1 to 64 bytes and meets the regular expression **"^[a-zA-Z0-9]{1,64}$"**.                                                           |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 0d0466b00d0466b00d0466b00d0466b0                                                                                                                                                         |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | operations         | Yes             | Array of strings | Permissions that can be granted. Values: **create-datakey**, **create-datakey-without-plaintext**, **encrypt-datakey**, **decrypt-datakey**, **describe-key**, **create-grant**, **retire-grant** |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | **create-grant** cannot be the only value.                                                                                                                                                        |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | issuing_principal  | Yes             | String           | Indicates the ID of the user who created the grant. The value is between 1 to 64 bytes and meets the regular expression **"^[a-zA-Z0-9]{1,64}$"**.                                                |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 0d0466b00d0466b00d0466b00d0466b0                                                                                                                                                         |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | creation_date      | Yes             | String           | Creation time. The value is a timestamp expressed in the number of seconds since 00:00:00 UTC on January 1, 1970.                                                                                 |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 1497341531000                                                                                                                                                                            |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name               | No              | String           | Name of a grant which can be 1 to 255 characters in length and matches the regular expression **^[a-zA-Z0-9:/_-]{1,255}$**                                                                        |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retiring_principal | No              | String           | Indicates the ID of the retiring user. The value is between 1 to 64 bytes and meets the regular expression **"^[a-zA-Z0-9]{1,64}$"**.                                                             |
   |                    |                 |                  |                                                                                                                                                                                                   |
   |                    |                 |                  | Example: 0d0466b00d0466b00d0466b00d0466b0                                                                                                                                                         |
   +--------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example
-------

The following example describes how to query the grant list of a CMK whose ID is **0d0466b0-e727-4d9c-b35d-f84bb474a37f**.

-  Example request

   .. code-block::

      {
          "key_id": "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
          "limit": "",
          "marker": ""
      }

-  Example response

   .. code-block::

      {
          "grants": [
           {"key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
            "grant_id": "7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d",
            "operations":
            ["describe-key","create-datakey", "encrypt-datakey"],
            "grantee_principal":"13gg44z4g2sglzk0egw0u726zoyzvrs8",
            "retiring_principal":"13gg44z4g2sglzk0egw0u726zoyzvrs8",
            "issuing_principal":"e4hkeeea506ex3wgnzyhi656n8hx8xa3",
            "name":"my_grant",
            "creation_date":"1497341531000",
            }],
          "next_marker": "",
          "truncated": "false",
          "total":1
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

:ref:`Table 6 <kms_02_0031__en-us_topic_0112992310_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0031__en-us_topic_0112992310_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 6** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
