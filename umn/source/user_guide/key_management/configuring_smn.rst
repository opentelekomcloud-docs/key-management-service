:original_name: kms_01_0021.html

.. _kms_01_0021:

Configuring SMN
===============

Scenario
--------

This section describes how to configure the Simple Message Notification (SMN) function on the Cloud Trace Service (CTS) console.

Decryption will fail if the CMK used has been scheduled for deletion. You will receive messages about the decryption failure on terminals (SMS, email, HTTP, or HTTPS) if the SMN function has been configured in CTS.

Prerequisites
-------------

-  CTS has been enabled.
-  You have subscribed to SMN.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Management & Deployment** > **Cloud Trace Service** to go to the CTS console.

#. In the navigation tree on the left, click **Tracker**.

#. If the desired tracker is not enabled, click **Enable**. In the dialog box that is displayed, click **OK** to enable the tracker. If the tracker is already enabled, skip this step.

#. In the navigation tree on the left, click **Key Event Notifications**. The **Key Event Notifications** page is displayed.

#. Click **Create Key Event Notification** at the upper right corner of the page. The creation page is displayed.

#. In the **Basic Information** area, enter a notification name. See :ref:`Figure 1 <kms_01_0021__fig197519401153>` for details.

   .. _kms_01_0021__fig197519401153:

   .. figure:: /_static/images/en-us_image_0129547803.png
      :alt: **Figure 1** Configuring basic information

      **Figure 1** Configuring basic information

#. Select operation types in the **Operation** area. See :ref:`Figure 2 <kms_01_0021__fig103085242037>` for details.

   .. _kms_01_0021__fig103085242037:

   .. figure:: /_static/images/en-us_image_0129548665.png
      :alt: **Figure 2** Selecting operation types

      **Figure 2** Selecting operation types

   .. table:: **Table 1** Parameters for operation types

      +----------------+-------------------------------------------------------------------------------------------------+---------------+
      | Parameter      | Description                                                                                     | Example Value |
      +================+=================================================================================================+===============+
      | Operation Type | SMN sends messages to users when deletion, creation, or login operations are performed on CMKs. | Delete        |
      +----------------+-------------------------------------------------------------------------------------------------+---------------+

#. In the **User** area, specify the user who performs the specified operations. See :ref:`Figure 3 <kms_01_0021__fig58261115592>` for details.

   .. note::

      -  You can select **All users** so that SMN notifications are sent when specified operations are performed by any user.
      -  You can also select **Specified users** and add users to the **User List**. Then SMN notifications are sent when the specified operations are performed by specified users.

   .. _kms_01_0021__fig58261115592:

   .. figure:: /_static/images/en-us_image_0129550097.png
      :alt: **Figure 3** Specifying users

      **Figure 3** Specifying users

#. In the **Topic** area, configure whether to send notifications. See :ref:`Figure 4 <kms_01_0021__fig14611311075>` for details.

   .. _kms_01_0021__fig14611311075:

   .. figure:: /_static/images/en-us_image_0129551027.png
      :alt: **Figure 4** Configuring SMN topic

      **Figure 4** Configuring SMN topic

   .. table:: **Table 2** Parameters for configuring the SMN notification

      +-----------------------+-----------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                 | Configuration         |
      +=======================+=============================================================================+=======================+
      | Send Notification     | Specifies whether notifications will be sent.                               | Yes                   |
      |                       |                                                                             |                       |
      |                       | -  Select **Yes** to activate notification.                                 |                       |
      |                       | -  Select **No** to deactivate notification.                                |                       |
      +-----------------------+-----------------------------------------------------------------------------+-----------------------+
      | SMN Topic             | You can select an existing topic or click **Topic** to create a topic.      | KMS                   |
      |                       |                                                                             |                       |
      |                       | For details about topics, see the *Simple Message Notification User Guide*. |                       |
      +-----------------------+-----------------------------------------------------------------------------+-----------------------+

#. Click **OK**. The SMN notification is configured.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
