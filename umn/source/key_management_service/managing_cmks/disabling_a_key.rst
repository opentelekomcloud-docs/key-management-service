:original_name: dew_01_0030.html

.. _dew_01_0030:

Disabling a Key
===============

This section describes how to use the KMS console to disable one or more custom keys, thereby protecting data in urgent cases.

After being disabled, a custom key cannot be used to encrypt or decrypt any data. Before using a disabled key to encrypt or decrypt data, you must enable it by following instructions in :ref:`Enabling a Key <dew_01_0029>`.

Prerequisites
-------------

The key you want to disable is in **Enabled** status.

Constraints
-----------

-  Default keys created by KMS cannot be disabled.
-  A disabled key is still billable. It will stop incurring charges if it is deleted.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| on the left and choose **Security** > **Key Management Service**.
#. Locate the target key in the list and click **Disable** in the **Operation** column.
#. In the displayed dialog box, select **I understand the impact of disabling keys**, and click **OK**.

   .. note::

      To disable multiple keys at a time, select them and click **Disable** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511517795.png
