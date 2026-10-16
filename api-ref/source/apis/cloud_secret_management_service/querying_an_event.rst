:original_name: ShowSecretEvent.html

.. _ShowSecretEvent:

Querying an Event
=================

Function
--------

Query information about a specified event.

Constraints
-----------

The information returned by this API is the metadata information value of the secret event notification.

URI
---

GET /v1/{project_id}/csms/events/{event_name}

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

.. table:: **Table 3** Response body parameter

   +-----------+------------------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                               | Description                |
   +===========+====================================================================================+============================+
   | event     | :ref:`Event <showsecretevent__en-us_topic_0000001771567581_response_event>` object | Event notification object. |
   +-----------+------------------------------------------------------------------------------------+----------------------------+

.. _showsecretevent__en-us_topic_0000001771567581_response_event:

.. table:: **Table 4** Event

   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                             | Description                                                                                                                                                              |
   +=======================+==================================================================================================+==========================================================================================================================================================================+
   | name                  | String                                                                                           | Event notification name.                                                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_id              | String                                                                                           | Indicates the resource identifier of the event notification.                                                                                                             |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_types           | Array of strings                                                                                 | Set the basic event type list.                                                                                                                                           |
   |                       |                                                                                                  |                                                                                                                                                                          |
   |                       |                                                                                                  | Constraint: The array can contain 1 to 12 items.                                                                                                                         |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                                                                                           | Event notification status. The value can be:                                                                                                                             |
   |                       |                                                                                                  |                                                                                                                                                                          |
   |                       |                                                                                                  | **ENABLED**                                                                                                                                                              |
   |                       |                                                                                                  |                                                                                                                                                                          |
   |                       |                                                                                                  | **DISABLED**                                                                                                                                                             |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                                                                                             | Time when an event notification is created. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time specified by this parameter. |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                                                                                             | Last update time of the event notification. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time.                             |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification          | :ref:`Notification <showsecretevent__en-us_topic_0000001771567581_response_notification>` object | Notification topic object.                                                                                                                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showsecretevent__en-us_topic_0000001771567581_response_notification:

.. table:: **Table 5** Notification

   +-------------+--------+-------------------------------------------------------------+
   | Parameter   | Type   | Description                                                 |
   +=============+========+=============================================================+
   | target_type | String | Type of the object to which an event notification is sent.  |
   +-------------+--------+-------------------------------------------------------------+
   | target_id   | String | ID of the object to which the event notification is sent.   |
   +-------------+--------+-------------------------------------------------------------+
   | target_name | String | Name of the object to which the event notification is sent. |
   +-------------+--------+-------------------------------------------------------------+

Example Request
---------------

Query the information about event **event-test**.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/csms/events/event-test

Example Response
----------------

.. code-block::

   {
     "event" : {
       "name" : "event-test",
       "event_id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "state" : "ENABLED",
       "event_types" : [ "SECRET_VERSION_EXPIRED" ],
       "create_time" : 1581507580000,
       "update_time" : 1581507580000,
       "notification" : {
         "target_type" : "SMN",
         "target_id" : "urn:smn:eu-de:SecertExpirationTest",
         "target_name" : "SecertExpirationNotificationTest"
       }
     }
   }

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
