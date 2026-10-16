:original_name: dew_01_2006.html

.. _dew_01_2006:

Creating an Event
=================

With event notification, you can understand the secret version changes. The notifications are in JSON format, which is applicable to automatic parsing in machine-machine scenarios. This section describes how to create an event on the **Events** page.

When creating an event, you can set the event type to new **Version creation**, **Version expiry**, **Secret rotation**, and **Secret deletion**.

Constraints
-----------

-  You can create up to 30 events.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Events**. The **Events** page is displayed.

#. Click **Create Event** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000002279494993.png
      :alt: **Figure 1** Creating an event

      **Figure 1** Creating an event

   .. table:: **Table 1** Parameters for creating an event

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                             |
      +===================================+=========================================================================================================================================+
      | Event Name                        | Name of the event to be created.                                                                                                        |
      |                                   |                                                                                                                                         |
      |                                   | .. note::                                                                                                                               |
      |                                   |                                                                                                                                         |
      |                                   |    Only letters, digits, hyphens (-), and underscores (_) are supported.                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | The options are **Enabled** and **Disabled**. By default, **Enabled** is selected.                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Topic Type/Name                   | Topic type: **SMN** is selected by default.                                                                                             |
      |                                   |                                                                                                                                         |
      |                                   | Topic name: name of the topic created in SMN.                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Message Type                      | **Simple Message Notification (SMN)**: When a selected event is triggered for the target secret, CSMS sends a notification through SMN. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Topic Name                        | Select a topic from the drop-down list or create a topic.                                                                               |
      |                                   |                                                                                                                                         |
      |                                   | For details about topics and subscriptions, see the *Simple Message Notification User Guide*.                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Message Template                  | (Optional) Select a message template created in SMN or leave it as **None**.                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Event Type                        | Supported event types, including **Version creation**, **Version expiry**, and **Secret deletion**.                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. View the created event in the event list. The default event status is **Enabled**.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
