:original_name: UpdateSecretEvent.html

.. _UpdateSecretEvent:

Updating an Event
=================

Function
--------

Update the metadata of a specified event. The following metadata can be updated: event enabling status, basic type list, and notification topic.

Constraints
-----------

This API can be used to modify only the metadata of secret event notifications.

URI
---

PUT /v1/{project_id}/csms/events/{event_name}

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                              | Description                                                           |
   +=================+=================+===================================================================================================+=======================================================================+
   | state           | No              | String                                                                                            | Event notification status. The value can be:                          |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | **ENABLED**                                                           |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | **DISABLED**                                                          |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | event_types     | No              | Array of strings                                                                                  | Basic event list of the notification. The event types are as follows: |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_VERSION_CREATED**: Version created.                       |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_VERSION_EXPIRED**: Version expired.                       |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_ROTATED**: Secret rotated.                                |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_DELETED**: Secret deleted.                                |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_ROTATED_FAILED**: Secret rotation failed.                 |
   |                 |                 |                                                                                                   |                                                                       |
   |                 |                 |                                                                                                   | The basic event types in the list must be unique.                     |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | notification    | No              | :ref:`Notification <updatesecretevent__en-us_topic_0000001723967118_request_notification>` object | Notification topic object.                                            |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

.. _updatesecretevent__en-us_topic_0000001723967118_request_notification:

.. table:: **Table 4** Notification

   +-------------+-----------+--------+-------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                 |
   +=============+===========+========+=============================================================+
   | target_type | Yes       | String | Type of the object to which an event notification is sent.  |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | target_id   | Yes       | String | ID of the object to which the event notification is sent.   |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | target_name | Yes       | String | Name of the object to which the event notification is sent. |
   +-------------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Response body parameter

   +-----------+--------------------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                                 | Description                |
   +===========+======================================================================================+============================+
   | event     | :ref:`Event <updatesecretevent__en-us_topic_0000001723967118_response_event>` object | Event notification object. |
   +-----------+--------------------------------------------------------------------------------------+----------------------------+

.. _updatesecretevent__en-us_topic_0000001723967118_response_event:

.. table:: **Table 6** Event

   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                               | Description                                                                                                                                                              |
   +=======================+====================================================================================================+==========================================================================================================================================================================+
   | name                  | String                                                                                             | Event notification name.                                                                                                                                                 |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_id              | String                                                                                             | Resource identifier of an event notification.                                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_types           | Array of strings                                                                                   | Set the basic event type list.                                                                                                                                           |
   |                       |                                                                                                    |                                                                                                                                                                          |
   |                       |                                                                                                    | Constraint: The array can contain 1 to 12 items.                                                                                                                         |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                                                                                             | Event notification status. The value can be:                                                                                                                             |
   |                       |                                                                                                    |                                                                                                                                                                          |
   |                       |                                                                                                    | **ENABLED**                                                                                                                                                              |
   |                       |                                                                                                    |                                                                                                                                                                          |
   |                       |                                                                                                    | **DISABLED**                                                                                                                                                             |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                                                                                               | Time when an event notification is created. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time specified by this parameter. |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                                                                                               | Last update time of the event notification. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time.                             |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification          | :ref:`Notification <updatesecretevent__en-us_topic_0000001723967118_response_notification>` object | Notification topic object.                                                                                                                                               |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _updatesecretevent__en-us_topic_0000001723967118_response_notification:

.. table:: **Table 7** Notification

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

Update the notification object information of the event **event-test**.

.. code-block:: text

   PUT https://{csms_endpoint}/v1/{project_id}/csms/events/event-test
   {
     "notification" : {
       "target_type" : "SMN",
       "target_id" : "demo-smn-id",
       "target_name" : "demo-smn-name"
     }
   }

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
