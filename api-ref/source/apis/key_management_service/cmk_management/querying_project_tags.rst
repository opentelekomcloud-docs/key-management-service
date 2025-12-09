:original_name: kms_02_0044.html

.. _kms_02_0044:

Querying Project Tags
=====================

Function
--------

This API enables you to query all tag sets of a specified project.

URI
---

-  URI format

   GET /v1.0/{project_id}/kms/tags

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

Responses
---------

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================================================+
   | tags            | Yes             | Array of objects | list of tags, including tag keys and tag values.                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | -  **key** indicates the tag key. A CMK can have a maximum of 10 keys, and each of them is unique and cannot be empty. A key cannot have duplicate values. The value of **key** contains a maximum of 36 characters. |
   |                 |                 |                  | -  **value** indicates the tag value. Each tag value can contain a maximum of 43 characters. The relationship between values is **AND**.                                                                             |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Examples
--------

The following example describes how to query project tags.

-  Example request

   None

-  Example response

   .. code-block::

      {            "tags": [
                   {
                     "key": "key1",
                     "values": [
                         "value1",
                         "value2"
                       ]
                    },
                   {
                     "key": "key2",
                     "values": [
                         "value1",
                         "value2"
                      ]
              }
      ]
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

:ref:`Table 4 <kms_02_0044__en-us_topic_0112992316_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0044__en-us_topic_0112992316_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
