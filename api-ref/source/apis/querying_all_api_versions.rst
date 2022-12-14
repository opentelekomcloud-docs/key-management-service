:original_name: kms_02_0048.html

.. _kms_02_0048:

Querying All API Versions
=========================

Function
--------

This API is used to query the API versions.

URI
---

-  URI format

   GET /

-  Parameter description

   None

Requests
--------

None

Responses
---------

.. table:: **Table 1** Response parameters

   +-----------+-----------+------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                  |
   +===========+===========+==================+==============================================================================================================+
   | versions  | Yes       | Array of objects | Version object list. For details, see :ref:`Table 2 <kms_02_0048__en-us_topic_0133150653_table95441953481>`. |
   +-----------+-----------+------------------+--------------------------------------------------------------------------------------------------------------+

.. _kms_02_0048__en-us_topic_0133150653_table95441953481:

.. table:: **Table 2** **versions** field description

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                  |
   +=================+=================+==================+==============================================================================================================================================================================+
   | id              | Yes             | String           | Version number, for example, **v1.0**                                                                                                                                        |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links           | Yes             | Array of objects | JSON object. For details, see :ref:`Table 3 <kms_02_0048__en-us_topic_0133150653_table525011561381>`.                                                                        |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version         | Yes             | String           | If the APIs of this version support microversions, the supported maximum microversion is returned. If the microversion is not supported, empty character string is returned. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | Yes             | String           | Version status. Valid values are as follows:                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                              |
   |                 |                 |                  | -  **CURRENT**: widely used version                                                                                                                                          |
   |                 |                 |                  | -  **SUPPORTED**: earlier version which is still supported                                                                                                                   |
   |                 |                 |                  | -  **DEPRECATED**: deprecated version which may be deleted later                                                                                                             |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated         | Yes             | String           | Version release time, which must be UTC time. For example, the release time of v1 is 2014-06-28T12:20:21Z.                                                                   |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_version     | No              | String           | If the APIs of this version support microversions, the supported minimum microversion is returned. If the microversion is not supported, empty character string is returned. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0048__en-us_topic_0133150653_table525011561381:

.. table:: **Table 3** **links** field description

   ========= ========= ====== ==============================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============================
   href      Yes       String API URL
   rel       Yes       String The default value is **self**.
   ========= ========= ====== ==============================

Examples
--------

The following describes how to query the version information.

-  Example request

   None

-  Example response

   .. code-block::

      {
         "versions":
          [
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

:ref:`Table 4 <kms_02_0048__en-us_topic_0133150653_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0048__en-us_topic_0133150653_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 4** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
