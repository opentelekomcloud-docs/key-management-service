:original_name: CreateSecretEvent.html

.. _CreateSecretEvent:

Creating an Event
=================

Function
--------

Create an event that can be configured on one or more secrets. When an event is enabled and the basic event type contained in the event is triggered on the secret, the cloud service sends the corresponding event notification to the notification topic specified by the event.

Constraints
-----------

The created event notification cannot be used alone. It must be configured on a specific secret. The service does not check the validity of the event notification object. If the object does not exist under the account, event notification fails.

URI
---

POST /v1/{project_id}/csms/events

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                              | Description                                                                                                           |
   +=================+=================+===================================================================================================+=======================================================================================================================+
   | name            | Yes             | String                                                                                            | Name of the created event notification.                                                                               |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | Constraint: The value can contain 1 to 64 characters and must match the regular expression **^[a-zA-Z0-9_-]{1,64}$**. |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | event_types     | Yes             | Array of strings                                                                                  | Basic event list of the notification. The event types are as follows:                                                 |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_VERSION_CREATED**: Version created.                                                                       |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_VERSION_EXPIRED**: Version expired.                                                                       |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_ROTATED**: Secret rotated.                                                                                |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_DELETED**: Secret deleted.                                                                                |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | -  **SECRET_ROTATED_FAILED**: Secret rotation failed.                                                                 |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | The basic event types in the list must be unique.                                                                     |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | state           | Yes             | String                                                                                            | Whether the event takes effect. The contained basic event types are returned only when this function is enabled.      |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | **ENABLED**                                                                                                           |
   |                 |                 |                                                                                                   |                                                                                                                       |
   |                 |                 |                                                                                                   | **DISABLED**                                                                                                          |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | notification    | Yes             | :ref:`Notification <createsecretevent__en-us_topic_0000001771486901_request_notification>` object | Notification topic object.                                                                                            |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+

.. _createsecretevent__en-us_topic_0000001771486901_request_notification:

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
   | event     | :ref:`Event <createsecretevent__en-us_topic_0000001771486901_response_event>` object | Event notification object. |
   +-----------+--------------------------------------------------------------------------------------+----------------------------+

.. _createsecretevent__en-us_topic_0000001771486901_response_event:

.. table:: **Table 6** Event

   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                               | Description                                                                                                                                                              |
   +=======================+====================================================================================================+==========================================================================================================================================================================+
   | name                  | String                                                                                             | Event notification name.                                                                                                                                                 |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_id              | String                                                                                             | Indicates the resource identifier of the event notification.                                                                                                             |
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
   | notification          | :ref:`Notification <createsecretevent__en-us_topic_0000001771486901_response_notification>` object | Notification topic object.                                                                                                                                               |
   +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createsecretevent__en-us_topic_0000001771486901_response_notification:

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

Create an event for secret **demo-event**. The event types include creating a secret version and secret version expiration. The event notification mode is SMN, and the notification topic is **demo-smn-name**.

.. code-block:: text

   POST https://{csms_endpoint}/v1/{project_id}/csms/events
   {
     "name" : "demo-event",
     "event_types" : [ "SECRET_VERSION_CREATED", "SECRET_VERSION_EXPIRED" ],
     "state" : "ENABLED",
     "notification" : {
       "target_type" : "SMN",
       "target_id" : "urn:smn:eu-de:dc3b7c85759141a991da17423c0f2068:test-poc",
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
       "event_types" : [ "SECRET_VERSION_CREATED", "SECRET_VERSION_EXPIRED" ],
       "create_time" : 1581507580000,
       "update_time" : 1581507580000,
       "notification" : {
         "target_type" : "SMN",
         "target_id" : "urn:smn:cn-north-4:SecertExpirationTest",
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
