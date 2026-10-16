:original_name: DeleteSecretEvent.html

.. _DeleteSecretEvent:

Deleting an Event Immediately
=============================

Function
--------

Delete a specified event immediately. The deleted event cannot be restored. An event cannot be deleted if it is referenced by a secret. Disassociate the event from the secret.

Constraints
-----------

Secrets deleted via this API cannot be restored.

URI
---

DELETE /v1/{project_id}/csms/events/{event_name}

.. table:: **Table 1** URI parameters

   ========== ========= ====== ========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ========================
   project_id Yes       String Project ID.
   event_name Yes       String Event notification name.
   ========== ========= ====== ========================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                           |
   +=================+=================+=================+=======================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                           |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | It can be obtained by calling the IAM API. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | X-Language      | Yes             | String          | Error code language of the API response. The value must be **en-us**.                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

Delete the **event-test** event immediately.

.. code-block:: text

   DELETE https://{csms_endpoint}/v1/{project_id}/csms/events/event-test

Example Response
----------------

None

Status Code
-----------

=========== ====== ==================
Status Code Status Description
=========== ====== ==================
200         OK     Request succeeded.
=========== ====== ==================

Error Code
----------

For details, see :ref:`Error Code <kms_02_8887>`.
