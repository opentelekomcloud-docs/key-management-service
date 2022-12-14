:original_name: kms_02_0049.html

.. _kms_02_0049:

Querying a Specified API Version
================================

Function
--------

This API is used to query the version of an API.

URI
---

-  URI format

   GET /{version_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      version_id Yes       String Version ID
      ========== ========= ====== ===========

Requests
--------

None

Responses
---------

.. table:: **Table 2** Response parameters

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                    |
   +===========+===========+==================+================================================================================================================+
   | version   | Yes       | Array of objects | Version information. For details, see :ref:`Table 3 <kms_02_0049__en-us_topic_0133150654_table5856932152840>`. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------+

.. _kms_02_0049__en-us_topic_0133150654_table5856932152840:

.. table:: **Table 3** **version** field data structure description

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                  |
   +=================+=================+==================+==============================================================================================================================================================================+
   | id              | Yes             | String           | Version number, for example, **v1.0**                                                                                                                                        |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links           | Yes             | Array of objects | JSON object. For details, see :ref:`Table 4 <kms_02_0049__en-us_topic_0133150654_table525011561381>`.                                                                        |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version         | Yes             | String           | If the APIs of this version support microversions, the supported maximum microversion is returned. If the microversion is not supported, empty character string is returned. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | Yes             | String           | Version status. Valid values are as follows:                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                              |
   |                 |                 |                  | -  **CURRENT**: widely used version                                                                                                                                          |
   |                 |                 |                  | -  **SUPPORTED**: earlier version which is still supported                                                                                                                   |
   |                 |                 |                  | -  **DEPRECATED**: deprecated version which may be deleted later                                                                                                             |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated         | Yes             | String           | Version release time, which must be UTC time. For example, the release time of v1.0 is 2014-06-28T12:20:21Z.                                                                 |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_version     | No              | String           | If the APIs of this version support microversions, the supported minimum microversion is returned. If the microversion is not supported, empty character string is returned. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0049__en-us_topic_0133150654_table525011561381:

.. table:: **Table 4** **links** field data structure description

   ========= ========= ====== ==============================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============================
   href      Yes       String API URL
   rel       Yes       String The default value is **self**.
   ========= ========= ====== ==============================

Examples
--------

The following uses the **v1.0** version as an example.

-  Example request

   None

-  Example response

   .. code-block::

      {
         "version":
              {
                  "id":"v1.0",
                  "links":
                  [
                      {

                          "href":"https://kms.eu-de.otc.t-systems.com/v1.0/",
                          "rel":"self"
                      }
                  ],
                  "min_version":"",
                  "status":"CURRENT",
                  "version":"",
                  "updated":"2018-09-05T08:18:05Z"
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

:ref:`Table 5 <kms_02_0049__en-us_topic_0133150654_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0049__en-us_topic_0133150654_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
