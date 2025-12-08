:original_name: dew_01_0032.html

.. _dew_01_0032:

Canceling the Scheduled Deletion of One or More CMKs
====================================================

This section describes how to use the KMS console to cancel the scheduled deletion of one or more custom keys prior to deletion execution. After the cancellation, the key is in **Disabled** status.

Prerequisites
-------------

The CMK for which you want to cancel the scheduled deletion is in **Pending deletion** status.

Procedure
---------

To cancel the deletion of multiple keys at a time, select them and click **Cancel Deletion** in the upper left corner of the list. The following describes how to cancel the scheduled deletion of a key.

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| on the left and choose **Security** > **Key Management Service**.
#. In the row containing the target CMK, click **Cancel Deletion**.
#. In the dialog box that is displayed, click **OK**.

   -  If a key is created on the KMS console, the status of the key changes to **Disabled** after its scheduled deletion is canceled. For details about how to enable the key, see :ref:`Enabling a Key <dew_01_0029>`.
   -  If the CMK is created using imported materials, its status becomes **Disabled** after the cancellation. To enable the CMK, see :ref:`Enabling a Key <dew_01_0029>`.
   -  If the CMK is created using imported materials and no key materials have been imported for it, its status becomes **Pending import** after the cancellation. To use the CMK, perform :ref:`Creating CMKs Using Imported Key Materials <dew_01_0142>`.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511597849.png
