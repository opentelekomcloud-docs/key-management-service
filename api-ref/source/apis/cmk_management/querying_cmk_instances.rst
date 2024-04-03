:original_name: kms_02_0042.html

.. _kms_02_0042:

Querying CMK Instances
======================

Function
--------

This API allows you to query CMK instances.

You can use the tag filtering function to query the detailed information about a specified CMK.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/resource_instances/action

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

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================================================================================================================================================================================================================+
   | tags            | No              | Array of objects | list of tags, including tag keys and tag values.                                                                                                                                                                                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | -  **key** indicates the tag key. A CMK can have a maximum of 10 keys, and each of them is unique and cannot be empty. A key cannot have duplicate values. The value of **key** contains a maximum of 36 characters.                                                                                                                   |
   |                 |                 |                  | -  **value** indicates the tag value. Each tag value can contain a maximum of 43 characters. The relationship between values is **AND**.                                                                                                                                                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String           | Number of queried records. If **action** is set to **count**, this parameter does not need to be set. If **action** is set to **filter**, the default value is **10**.                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | The value ranges from 1 to 1000.                                                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String           | Index location. The query starts from the next piece of data indexed by this parameter. When data on the first page is queried, the value of this parameter queried on previous page is contained. If **action** is **count**, this parameter does not need to be set. If **action** is set to **filter**, the default value is **0**. |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | The value must be a numeral and cannot be a negative number.                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | Operation ID, which can be set to **filter** or **count**.                                                                                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | -  **filter**: indicates filtering.                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | -  **count**: indicates the number of queried records.                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of objects | Search field.                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | -  **key** indicates the field to be matched, for example, **resource_name**.                                                                                                                                                                                                                                                          |
   |                 |                 |                  | -  **value** indicates the value to be matched, which contains a maximum of 255 characters and cannot be empty.                                                                                                                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String           | 36-byte serial number of a request message                                                                                                                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                  | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                                                                                                                                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-------------+-----------+------------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type             | Description                                                                                                      |
   +=============+===========+==================+==================================================================================================================+
   | resources   | Yes       | Array of objects | Resource instance list. For details, see :ref:`Table 4 <kms_02_0042__en-us_topic_0112992313_table824381161412>`. |
   +-------------+-----------+------------------+------------------------------------------------------------------------------------------------------------------+
   | total_count | Yes       | Integer          | Total number of records                                                                                          |
   +-------------+-----------+------------------+------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0042__en-us_topic_0112992313_table824381161412:

.. table:: **Table 4** **resource** field description

   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type             | Description                                                                                                                |
   +=================+===========+==================+============================================================================================================================+
   | resource_id     | Yes       | String           | Resource ID                                                                                                                |
   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | resource_detail | Yes       | Object           | Resource details. For details, see :ref:`Table 4 <kms_02_0018__en-us_topic_0112992343_t98d238e10953421e84a073707024c329>`. |
   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | tags            | Yes       | Array of objects | Lists of tags. If there is no tag, the array is empty by default.                                                          |
   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+
   | resource_name   | Yes       | String           | Resource name. This parameter is an empty string by default.                                                               |
   +-----------------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------+

Examples
--------

The following example describes how to query key instances.

-  Example request

   .. code-block::

         {
                "offset": "100",
                "limit": "100",
                "action": "filter",
                "matches":[
                {
                         "key": "resource_name",
                         "value": "resource1"
                      }
                 ],
                "tags": [
                     {
                         "key": "key1",
                         "values": [
                                  "value1",
                                  "value2"
                         ]
                     }
                ]
           }

-  Example response

   .. code-block::

      {
       "resources": [{
             "resource_id": "90c03e67-5534-4ed0-acfa-89780e47a535",
             "resource_detail": {
                    "key_id": "90c03e67-5534-4ed0-acfa-89780e47a535",
                    "domain_id": "4B688Fb77412Aee5570E7ecdbeB5afdc",
                    "key_alias": "tagTest_xmdmi",
                    "key_description": "123",
                    "creation_date": 1521449277000,
                    "scheduled_deletion_date": "",
                    "key_state": 2,
                    "default_key_flag": 0,
                    "key_type": 1
             },
             "resource_name": "tagTest_xmdmi",
             "tags": [{
                    "key": "$",
                    "value": "testValue!"
             }, {
                    "key": "1",
                    "value": "ccwZ"
             }, {
                    "key": "1&",
                    "value": "testValue!"
             }, {
                    "key": "abcd",
                    "value": "1&"
             }, {
                    "key": "efg",
                    "value": "1&"
             }, {
                    "key": "faregbqer",
                    "value": "AAaa00-99"
             }, {
                    "key": "fcwefwq",
                    "value": "$"
             }, {
                    "key": "fwqegqwrg",
                    "value": "1&"
             }, {
                    "key": "haha",
                    "value": "qzzahnzgoqbkabppdehnbrrgbrkvlxkkfoosqyhdylq"
             }, {
                    "key": "quapxpysduboguiluwargcgmvcgxinianbhl",
                    "value": "testValue!"
             }]
       }]
       "total_count": "1"}

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

:ref:`Table 5 <kms_02_0042__en-us_topic_0112992313_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0042__en-us_topic_0112992313_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
