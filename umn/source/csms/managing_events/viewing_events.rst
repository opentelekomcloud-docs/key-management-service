:original_name: dew_01_2008.html

.. _dew_01_2008:

Viewing Events
==============

This section describes how to view the information about the created events on the **Events** page, including the event name, status, subscription event type, topic type/name, and creation time.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Events**. The **Events** page is displayed.

#. In the event list, view the event information. :ref:`Table 1 <dew_01_2008__table14496736144815>` describes the parameters in the event list.

   .. _dew_01_2008__table14496736144815:

   .. table:: **Table 1** Parameters in the event list

      +-----------------------------------+---------------------------------------------------------------------------+
      | Parameter                         | Description                                                               |
      +===================================+===========================================================================+
      | Event Name                        | Name of an event                                                          |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Status                            | Event status, including:                                                  |
      |                                   |                                                                           |
      |                                   | -  **Enabled**                                                            |
      |                                   | -  **Disabled**                                                           |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Subscription                      | Event type selected during event creation. The value can be:              |
      |                                   |                                                                           |
      |                                   | -  **Version creation**                                                   |
      |                                   | -  **Version expiry**                                                     |
      |                                   | -  **Secret deletion**                                                    |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Message/Name/Template             | **Message Type**: The value can be **Simple Message Notification (SMN)**. |
      |                                   |                                                                           |
      |                                   | **Event Name**: Enter the name of the topic created in SMN.               |
      |                                   |                                                                           |
      |                                   | **Message Template**: Select the message template created in SMN.         |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Created                           | Time when the event is created                                            |
      +-----------------------------------+---------------------------------------------------------------------------+

#. Click the event name to view its details.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
