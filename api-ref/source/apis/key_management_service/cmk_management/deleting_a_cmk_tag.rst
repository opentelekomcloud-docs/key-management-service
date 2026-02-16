:original_name: kms_02_0047.html

.. _kms_02_0047:

Deleting a CMK Tag
==================

Function
--------

This API enables you to delete a CMK tag.

URI
---

-  URI format

   DELETE /v1.0/{project_id}/kms/{key_id}/tags/{key}

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
      | key             | Yes             | String          | Tag key                                                                                                                    |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

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

None

Examples
--------

In the **0d0466b0e7274d9cb35df84bb474a37f** project, delete the tag whose key value is **testKey** from the **bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e** key.

-  Request example

   .. code-block::

      /v1.0/0d0466b0e7274d9cb35df84bb474a37f/kms/bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e/tags/testKey

-  Response example

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

:ref:`Table 3 <kms_02_0047__en-us_topic_0112992314_en-us_topic_0112992301_table3885195311010>` lists the normal status code returned by the response.

.. _kms_02_0047__en-us_topic_0112992314_en-us_topic_0112992301_table3885195311010:

.. table:: **Table 3** Status codes

   +-------------+------------+-------------------------------------------------------------------+
   | Status Code | Status     | Description                                                       |
   +=============+============+===================================================================+
   | 204         | No Content | The request is processed successfully and no content is returned. |
   +-------------+------------+-------------------------------------------------------------------+

Exception status code. For details, see :ref:`Status Codes <kms_02_0301>`.
