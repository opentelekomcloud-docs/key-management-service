:original_name: kms_02_0017.html

.. _kms_02_0017:

Querying the List of CMKs
=========================

Function
--------

This API allows you to query the list of all CMKs.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/list-keys

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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================================================================================================================================================================================+
   | limit           | No              | String          | This parameter specifies the number of entries returned. If the specified number is smaller than the actual number of existing entries, **true** will be returned for the response parameter **truncated**, indicating that the query results will be displayed in separate pages. The value is within the range of the maximum number of CMKs, for example, **100**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | This parameter marks the starting location in a pagination query. If the **truncated** value is **true**, you can send consecutive requests to obtain more record entries. The **marker** value must be set to the **next_marker** value in the response, for example, **10**.                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_state       | No              | String          | State of a CMK that matches the regular expression **^[1-5]{1}$**. The following values are enumerated:                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  **1** indicates that the CMK is waiting to be activated.                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **2** indicates that the CMK is enabled.                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **3** indicates that the CMK is disabled.                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 | -  **4** indicates that the CMK is scheduled for deletion.                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  **5** indicates that the CMK is waiting to be imported.                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                |
   +=================+=================+==================+============================================================================================================================================================================================+
   | keys            | Yes             | Array of strings | List of CMK IDs                                                                                                                                                                            |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_details     | Yes             | Array of objects | Key details list. For details, see :ref:`Table 4 <kms_02_0018__en-us_topic_0112992343_t98d238e10953421e84a073707024c329>`.                                                                 |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | next_marker     | Yes             | String           | This parameter indicates the **marker** value required for obtaining the next page of query results. If the **truncated** value is **false**, the **next_marker** parameter is left blank. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | total           | Yes             | Integer          | Total number of keys.                                                                                                                                                                      |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | truncated       | Yes             | String           | This parameter indicates whether there are more results displayed in another page.                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                            |
   |                 |                 |                  | -  If the value is **true**, there are more results.                                                                                                                                       |
   |                 |                 |                  | -  If the value is **false**, the current page is the last page.                                                                                                                           |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Examples
--------

The following shows an example when **limit** is set to **2** and **marker** is set to **1**.

-  Example request

   .. code-block::

      {
          "limit": "2",
          "marker": "1"
      }

-  Example response

   .. code-block::

      {
          "keys": [
              "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
              "2e258389-bb1e-4568-a1d5-e1f50adf70ea"
          ],
          "key_details": [
              {
              "key_id":"0d0466b0-e727-4d9c-b35d-f84bb474a37f",
              "domain_id":"00074811d5c27c4f8d48bb91e4a1dcfd",
              "key_alias":"caseuirpr",
              "realm":"aaaa",
              "key_description":"123",
              "creation_date":"1502799822000",
              "scheduled_deletion_date":"",
              "key_state":"2",
              "default_key_flag":"0",
              "key_type":"1",
              "expiration_time":"1501578672000",
              "origin":"kms"
      },
              {
              "key_id":"2e258389-bb1e-4568-a1d5-e1f50adf70ea",
              "domain_id":"00074811d5c27c4f8d48bb91e4a1dcfd",
              "key_alias":"casehvniz",
              "realm":"aaaa",
              "key_description":"234",
              "creation_date":"1502799820000",
              "scheduled_deletion_date":"",
              "key_state":"2",
              "default_key_flag":"0",
              "key_type":"1",
              "expiration_time":"1501578673000",
              "origin":"kms"
      }
           ],
          "next_marker": "",
          "truncated": "false",
          "total":2
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

:ref:`Table 4 <kms_02_0017__en-us_topic_0112992332_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0017__en-us_topic_0112992332_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
