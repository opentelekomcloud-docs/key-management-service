:original_name: kms_02_0025.html

.. _kms_02_0025:

Querying the Quota of a User
============================

Function
--------

This API is used to query the quota of a user, that is, the allocated total number of CMKs that can be created by a user and the number of CMKs that has been created by the user.

.. note::

   The quota does not include Default Master Keys.

URI
---

-  URI format

   GET /v1.0/{project_id}/kms/user-quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Requests
--------

None

Responses
---------

.. table:: **Table 2** Response parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                         |
   +===========+===========+========+=====================================================================================================+
   | quotas    | Yes       | Object | Quota list. For details, see :ref:`Table 3 <kms_02_0025__en-us_topic_0112992292_table91213810301>`. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+

.. _kms_02_0025__en-us_topic_0112992292_table91213810301:

.. table:: **Table 3** **quotas** field description

   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                   |
   +===========+===========+==================+===============================================================================================================+
   | resources | Yes       | Array of objects | Resource quota list. For details, see :ref:`Table 4 <kms_02_0025__en-us_topic_0112992292_table167809412315>`. |
   +-----------+-----------+------------------+---------------------------------------------------------------------------------------------------------------+

.. _kms_02_0025__en-us_topic_0112992292_table167809412315:

.. table:: **Table 4** **resources** field description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                       |
   +=================+=================+=================+===================================================================================+
   | type            | Yes             | String          | Quota type.                                                                       |
   |                 |                 |                 |                                                                                   |
   |                 |                 |                 | Enumerated values:                                                                |
   |                 |                 |                 |                                                                                   |
   |                 |                 |                 | -  **CMK** indicates a Customer Master Key.                                       |
   |                 |                 |                 | -  **grant_per_CMK** indicates the number of grants that can be created on a CMK. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
   | used            | Yes             | Integer         | Used quota                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
   | quota           | Yes             | Integer         | Total quota                                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+

Examples
--------

-  Example request

   None

-  Example response

   .. code-block::

      {
          "quotas": {
              "resources": [
                  {
                      "type": "CMK",
                      "used": 15,
                      "quota": 20
                  },
                  {
                      "type": "grant_per_CMK",
                      "used": 15,
                      "quota": 100
                  }

              ]
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

:ref:`Table 5 <kms_02_0025__en-us_topic_0112992292_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0025__en-us_topic_0112992292_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
