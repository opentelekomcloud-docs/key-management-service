:original_name: kms_02_0043.html

.. _kms_02_0043:

Querying CMK Tags
=================

Function
--------

This API allows you to query tags of a specified CMK.

TMS may use this API to query all tags of a specified CMK.

URI
---

-  URI format

   GET /v1.0/{project_id}/kms/{key_id}/tags

-  Parameter description

   .. table:: **Table 1** Parameter description

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

None

Responses
---------

.. table:: **Table 2** Response parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================================================+
   | tags            | Yes             | Array of objects | list of tags, including tag keys and tag values.                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | -  **key** indicates the tag key. A CMK can have a maximum of 10 keys, and each of them is unique and cannot be empty. A key cannot have duplicate values. The value of **key** contains a maximum of 36 characters. |
   |                 |                 |                  | -  **value** indicates the tag value. Each tag value can contain a maximum of 43 characters. The relationship between values is **AND**.                                                                             |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | existTagNum     | Yes             | Integer          | Number of key tags.                                                                                                                                                                                                  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Examples
--------

The following example describes how to query CMK tags.

-  Example request

   None

-  Example response

   .. code-block::

      {         "tags": [
                 {
                  "key": "key1",
                  "value": "value1"
                 },
                 {
                  "key": "key2",
                  "value": "value3"
                 }
                 ],
                 "existTagsNum":2
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

:ref:`Table 3 <kms_02_0043__en-us_topic_0112992321_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0043__en-us_topic_0112992321_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 3** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
