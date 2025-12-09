:original_name: kms_02_0045.html

.. _kms_02_0045:

Adding or Deleting CMK Tags in Batches
======================================

Function
--------

This API enables you to add or delete CMK tags in batches.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/{key_id}/tags/action

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                |
      +=================+=================+=================+============================================================================================================================+
      | project_id      | Yes             | String          | Project ID                                                                                                                 |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
      | key_id          | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** |
      |                 |                 |                 |                                                                                                                            |
      |                 |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                              |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Requests
--------

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

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================================================+
   | tags            | Yes             | Array of objects | Tag list, which is the value pairs of **key** and **value**.                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | -  **key** indicates the tag key. A CMK can have a maximum of 10 keys, and each of them is unique and cannot be empty. A key cannot have duplicate values. The value of **key** contains a maximum of 36 characters. |
   |                 |                 |                  | -  **value** indicates the tag value. Each tag value can contain a maximum of 43 characters. The relationship between values is **AND**.                                                                             |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | Operation ID.                                                                                                                                                                                                        |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | The value can be **create** or **delete**.                                                                                                                                                                           |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String           | 36-byte serial number of a request message                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

None

Examples
--------

The following example describes how to add tags, the keys and values of which are **key1**, **key**, **value1**, and **value3** respectively.

-  Example request

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key",
                  "value": "value3"
              }
          ]
      }

   or

   .. code-block::

      {
          "action": "delete",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
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

:ref:`Table 4 <kms_02_0045__en-us_topic_0112992301_table3885195311010>` lists the normal status code returned by the response.

.. _kms_02_0045__en-us_topic_0112992301_table3885195311010:

.. table:: **Table 4** Status codes

   +-------------+------------+-------------------------------------------------------------------+
   | Status Code | Status     | Description                                                       |
   +=============+============+===================================================================+
   | 204         | No Content | The request is processed successfully and no content is returned. |
   +-------------+------------+-------------------------------------------------------------------+

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
