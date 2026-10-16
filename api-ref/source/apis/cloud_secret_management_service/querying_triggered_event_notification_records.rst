:original_name: ListNotificationRecords.html

.. _ListNotificationRecords:

Querying Triggered Event Notification Records
=============================================

Function
--------

Query all event notification records triggered in the last three months.

Constraints
-----------

Only event notification records generated within three months are stored.

URI
---

GET /v1/{project_id}/csms/notification-records

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

Response Parameters
-------------------

.. table:: **Table 3** Response body parameters

   +-----------+--------------------------------------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                                                   | Description             |
   +===========+========================================================================================================+=========================+
   | records   | Array of :ref:`Record <listnotificationrecords__en-us_topic_0000001771567585_response_record>` objects | Record object.          |
   +-----------+--------------------------------------------------------------------------------------------------------+-------------------------+
   | page_info | :ref:`PageInfo <listnotificationrecords__en-us_topic_0000001771567585_response_pageinfo>` object       | Pagination information. |
   +-----------+--------------------------------------------------------------------------------------------------------+-------------------------+

.. _listnotificationrecords__en-us_topic_0000001771567585_response_record:

.. table:: **Table 4** Record

   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                  | Description                                                                                                                                                                     |
   +==========================+=======================+=================================================================================================================================================================================+
   | event_name               | String                | Secret name.                                                                                                                                                                    |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | trigger_event_type       | String                | Event type.                                                                                                                                                                     |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SECRET_VERSION_CREATED**: Version created.                                                                                                                                 |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SECRET_VERSION_EXPIRED**: Version expired.                                                                                                                                 |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SECRET_ROTATED**: Secret rotated.                                                                                                                                          |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SECRET_DELETED**: Secret deleted.                                                                                                                                          |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SECRET_ROTATED_FAILED**: Secret rotation failed.                                                                                                                           |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time              | Long                  | Time when an event notification record is created. The value is a timestamp, that is, the total number of seconds from January 1, 1970 to the time specified by this parameter. |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_name              | String                | Secret name.                                                                                                                                                                    |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_type              | String                | Secret type.                                                                                                                                                                    |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **COMMON**: shared secret (default). It is used to store sensitive information in an application system.                                                                     |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **RDS**: RDS secret. It is used to store RDS account information. (This type is no longer supported and has been replaced by **RDS-FG**.)                                    |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **RDS-FG**: RDS secret. It is used to store RDS account information.                                                                                                         |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **GaussDB-FG**: TaurusDB secret. It is used to store TaurusDB account information.                                                                                           |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_target_name | String                | Name of the object to which the event notification is sent.                                                                                                                     |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_target_id   | String                | ID of the object to which the event notification is sent.                                                                                                                       |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_content     | String                | Event notification.                                                                                                                                                             |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_status      | String                | Event notification status.                                                                                                                                                      |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **SUCCESS**: Event notification succeeded.                                                                                                                                   |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **FAIL**: Event notification failed.                                                                                                                                         |
   |                          |                       |                                                                                                                                                                                 |
   |                          |                       | -  **INVALID**: Failed to send the event notification because the topic is invalid or incorrect.                                                                                |
   +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listnotificationrecords__en-us_topic_0000001771567585_response_pageinfo:

.. table:: **Table 5** PageInfo

   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                                |
   +=================+=========+============================================================================================================+
   | next_marker     | String  | Query address of the next page (secret name at the end of the current page and the start of the next page) |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | previous_marker | String  | Secret name at the start of the current page and the end of the last page                                  |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+
   | current_count   | Integer | Number of records returned on the current page.                                                            |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query all event notification records triggered in the last three months.

.. code-block:: text

   GET https://{csms_endpoint}/v1/{project_id}/csms/notification-records

Example Response
----------------

.. code-block::

   {
     "records" : [ {
       "event_name" : "demo-event",
       "trigger_event_type" : "SECRET_VERSION_EXPIRED",
       "create_time" : 1581507580000,
       "secret_name" : "demo-secret",
       "secret_type" : "COMMON",
       "notification_target_name" : "SecertExpirationNotificationTest",
       "notification_target_id" : "urn:smn:eu-de:SecertExpirationTest",
       "notification_content" : "{\"eventName\":\"TestEvent20221112\",\"eventType\":\"SECRET_VERSION_EXPIRED\",\"eventTime\":\"2023-04-14T20:25:10.126Z\",\"data\":{\"secretId\":\"fde3d6ba-cb31-40b0-b6c4-78757050f8c8\",\"secretName\":\"Secret20230325\",\"createTime\":\"2023-03-22T20:43:04.000Z\",\"updateTime\":\"2023-04-14T20:18:29.000Z\",\"versionId\":\"v18\",\"versionExpireTime\":\"2023-03-29T17:07:23.000Z\"}}",
       "notification_status" : "SUCCESS"
     } ]
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
