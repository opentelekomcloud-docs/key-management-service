:original_name: kms_02_0032.html

.. _kms_02_0032:

Querying Grants That Can Be Retired
===================================

Function
--------

This API enables you to query grants that can be retired.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/list-retirable-grants

-  Parameter description

   .. table:: **Table 1** URI parameter

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Requests
--------

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
   | limit           | No              | String          | This parameter specifies the number of entries returned. If the specified number is smaller than the actual number of existing entries, **true** will be returned for the response parameter **truncated**, indicating that the query results will be displayed in separate pages. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | The value is within the range of the maximum number of grants, for example, **100**.                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | This parameter marks the starting location in a pagination query.                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | If the **truncated** value is **true**, you can send consecutive requests to obtain more record entries. The **marker** value must be set to the **next_marker** value in the response, for example, **10**.                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

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

Examples
--------

The following example describes how to query the list of grants that can be retired.

-  Example request

   .. code-block::

      {
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
            "creation_date":"1497341531000"
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

:ref:`Table 5 <kms_02_0032__en-us_topic_0112992293_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0032__en-us_topic_0112992293_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
