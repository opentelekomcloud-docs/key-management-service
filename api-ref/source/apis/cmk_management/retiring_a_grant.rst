:original_name: kms_02_0030.html

.. _kms_02_0030:

Retiring a Grant
================

Function
--------

This API enables users to retire a grant.

For example, user A grants operation permissions on CMK **A/key** to user B and authorizes user C to retire the grant. By doing this, users A, B, and C all can cancel the permissions. After the canceling, user B does not have permissions on CMK **A/key** anymore.

.. important::

   The following are allowed to call this API:

   -  The user who granted the permissions
   -  The user indicated by parameter **retiring_principal**
   -  The user indicated by parameter **grantee_principal** when **retire-grant** has been selected

URI
---

-  URI format

   POST /v1.0/{project_id}/kms/retire-grant

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

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | key_id          | Yes             | String          | 36-byte ID of a CMK that matches the regular expression **^[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}$** |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Example: 0d0466b0-e727-4d9c-b35d-f84bb474a37f                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | grant_id        | Yes             | String          | 64-byte ID of a grant that meets the regular expression **^[A-Fa-f0-9]{64}$**                                              |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Example: 7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | sequence        | No              | String          | 36-byte serial number of a request message                                                                                 |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Example: 919c82d4-8046-4722-9094-35c3c6524cff                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Responses
---------

None

Examples
--------

The following example describes how to retire a grant whose grant ID is **7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d** and the CMK ID is **bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e**.

-  Example request

   .. code-block::

      {
          "key_id": "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
          "grant_id":"7c9a3286af4fcca5f0a385ad13e1d21a50e27b6dbcab50f37f30f93b8939827d"
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

:ref:`Table 3 <kms_02_0030__en-us_topic_0112992299_en-us_topic_0112992294_en-us_topic_0079615001_table20596071>` lists the normal status code returned by the response.

.. _kms_02_0030__en-us_topic_0112992299_en-us_topic_0112992294_en-us_topic_0079615001_table20596071:

.. table:: **Table 3** Status codes

   =========== ====== ===============================
   Status Code Status Description
   =========== ====== ===============================
   200         OK     Request processed successfully.
   =========== ====== ===============================

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
