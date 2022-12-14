:original_name: kms_02_0024.html

.. _kms_02_0024:

Querying the Number of Instances
================================

Function
--------

This API is used to query the number of instances, that is, the number of CMKs created.

.. note::

   Default Master Keys are automatically created by services and are not included in this query.

URI
---

-  URI format

   GET /v1.0/{project_id}/kms/user-instances

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

   ============ ========= ======= ==========================
   Parameter    Mandatory Type    Description
   ============ ========= ======= ==========================
   instance_num Yes       Integer Number of non-default CMKs
   ============ ========= ======= ==========================

Examples
--------

-  Example request

   None

-  Example response

   .. code-block::

      {
          "instance_num": 15
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

:ref:`Table 3 <kms_02_0024__en-us_topic_0112992320_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0024__en-us_topic_0112992320_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 3** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
