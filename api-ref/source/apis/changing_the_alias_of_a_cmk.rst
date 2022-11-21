:original_name: kms_02_0026.html

.. _kms_02_0026:

Changing the Alias of a CMK
===========================

Function
--------

This API enables you to change the alias of a CMK.

.. note::

   -  A Default Master Key (the alias suffix of which is **/default**) does not allow alias changes.
   -  A CMK in **Scheduled deletion** status does not allow alias changes.

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/update-key-alias

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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================+
   | key_id          | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$**                                            |
   |                 |                 |                 |                                                                                                                                                                       |
   |                 |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_alias       | Yes             | String          | Alias of a CMK whose length is 1 to 255 characters and which matches the regular expression **^[a-zA-Z0-9:/_-]{1,255}$**. Suffix of the alias cannot be **/default**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                       |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

.. table:: **Table 3** Response parameters

   +-----------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                       |
   +===========+===========+==================+===================================================================================================================+
   | key_info  | Yes       | Array of objects | Information about keys. For details, see :ref:`Table 4 <kms_02_0026__en-us_topic_0112992307_table4661953591125>`. |
   +-----------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------+

.. _kms_02_0026__en-us_topic_0112992307_table4661953591125:

.. table:: **Table 4** **key_info** field description

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   key_id    Yes       String CMK ID
   key_alias Yes       String Alias of a CMK
   ========= ========= ====== ==============

Examples
--------

The following is an example about how to modify a CMK whose alias ID is **bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e** and alias is **test**.

-  Example request

   .. code-block::

      {
          "key_alias": "test",
          "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e"
      }

-  Example response

   .. code-block::

      {
          "key_info": {
              "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
              "key_alias": "test"
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

:ref:`Table 5 <kms_02_0026__en-us_topic_0112992307_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0026__en-us_topic_0112992307_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 5** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
