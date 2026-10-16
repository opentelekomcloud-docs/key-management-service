:original_name: ListSecretEvents.html

.. _ListSecretEvents:

Querying the Event List
=======================

Function
--------

Obtain all events created by the current user in the project.

Constraints
-----------

The information returned by this API is the metadata information of the event notification, excluding the secret value.

URI
---

GET /v1/{project_id}/csms/events

.. table:: **Table 1** URI parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | limit           | No              | String          | Number of results returned on each page.                                                               |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Default value: **50**                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Start event name of pagination query. If this parameter is left blank, only the first page is queried. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                                          | Description             |
   +===========+===============================================================================================+=========================+
   | events    | Array of :ref:`Event <listsecretevents__en-us_topic_0000001723807750_response_event>` objects | Event details list.     |
   +-----------+-----------------------------------------------------------------------------------------------+-------------------------+
   | page_info | :ref:`PageInfo <listsecretevents__en-us_topic_0000001723807750_response_pageinfo>` object     | Pagination information. |
   +-----------+-----------------------------------------------------------------------------------------------+-------------------------+

.. _listsecretevents__en-us_topic_0000001723807750_response_event:

.. table:: **Table 5** Event

   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                              | Description                                                                                                                                                              |
   +=======================+===================================================================================================+==========================================================================================================================================================================+
   | name                  | String                                                                                            | Event notification name.                                                                                                                                                 |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_id              | String                                                                                            | Indicates the resource identifier of the event notification.                                                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_types           | Array of strings                                                                                  | Set the basic event type list.                                                                                                                                           |
   |                       |                                                                                                   |                                                                                                                                                                          |
   |                       |                                                                                                   | Constraint: The array can contain 1 to 12 items.                                                                                                                         |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | state                 | String                                                                                            | Event notification status. The value can be:                                                                                                                             |
   |                       |                                                                                                   |                                                                                                                                                                          |
   |                       |                                                                                                   | **ENABLED**                                                                                                                                                              |
   |                       |                                                                                                   |                                                                                                                                                                          |
   |                       |                                                                                                   | **DISABLED**                                                                                                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                                                                                              | Time when an event notification is created. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time specified by this parameter. |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                                                                                              | Last update time of the event notification. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time.                             |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification          | :ref:`Notification <listsecretevents__en-us_topic_0000001723807750_response_notification>` object | Notification topic object.                                                                                                                                               |
   +-----------------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listsecretevents__en-us_topic_0000001723807750_response_notification:

.. table:: **Table 6** Notification

   +-------------+--------+-------------------------------------------------------------+
   | Parameter   | Type   | Description                                                 |
   +=============+========+=============================================================+
   | target_type | String | Type of the object to which an event notification is sent.  |
   +-------------+--------+-------------------------------------------------------------+
   | target_id   | String | ID of the object to which the event notification is sent.   |
   +-------------+--------+-------------------------------------------------------------+
   | target_name | String | Name of the object to which the event notification is sent. |
   +-------------+--------+-------------------------------------------------------------+

.. _listsecretevents__en-us_topic_0000001723807750_response_pageinfo:

.. table:: **Table 7** PageInfo

   +-----------------+---------+-------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                                 |
   +=================+=========+=============================================================================================================+
   | next_marker     | String  | Query address of the next page (secret name at the end of the current page and the start of the next page). |
   +-----------------+---------+-------------------------------------------------------------------------------------------------------------+
   | previous_marker | String  | Secret name at the start of the current page and the end of the last page.                                  |
   +-----------------+---------+-------------------------------------------------------------------------------------------------------------+
   | current_count   | Integer | Number of records returned on the current page.                                                             |
   +-----------------+---------+-------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Obtain all events created by the current user in the project.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/csms/events

Example Response
----------------

.. code-block::

   {
     "events" : [ {
       "state" : "ENABLED",
       "name" : "TestEvent1",
       "event_id" : "120eeafd-eca5-4098-8733-c1b369f3a450",
       "event_types" : [ "SECRET_VERSION_CREATED", "SECRET_VERSION_EXPIRED", "SECRET_VERSION_NEAR_EXPIRY", "SECRET_DELETED" ],
       "create_time" : 1669042498000,
       "update_time" : 1669042498000,
       "notification" : {
         "target_type" : "SMN",
         "target_id" : "urn:smn:eu-de:dc3b7c85759141a991da17423c0f2068:smn-target-name",
         "target_name" : "smn-target-name"
       }
     }, {
       "state" : "ENABLED",
       "name" : "TestEvent2",
       "event_id" : "1d251c99-37d2-4396-86ce-f000d3aa9850",
       "event_types" : [ "SECRET_VERSION_CREATED", "SECRET_VERSION_EXPIRED", "SECRET_VERSION_NEAR_EXPIRY", "SECRET_DELETED" ],
       "create_time" : 1669041491000,
       "update_time" : 1669041491000,
       "notification" : {
         "target_type" : "SMN",
         "target_id" : "urn:smn:eu-de:dc3b7c85759141a991da17423c0f2068:smn-target-name",
         "target_name" : "smn-target-name"
       }
     } ],
     "page_info" : {
       "next_marker" : "TestEvent2",
       "previous_marker" : "TestEvent3",
       "current_count" : 2
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
