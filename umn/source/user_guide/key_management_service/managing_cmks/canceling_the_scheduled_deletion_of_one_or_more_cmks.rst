:original_name: kms_01_0032.html

.. _kms_01_0032:

Canceling the Scheduled Deletion of One or More CMKs
====================================================

This section describes how to use the KMS console to cancel the scheduled deletion of one or more custom keys prior to deletion execution. After the cancellation, the key is in **Disabled** status.

Prerequisites
-------------

The CMK for which you want to cancel the scheduled deletion is in **Pending deletion** status.

Procedure
---------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.
#. In the row containing the target CMK, click **Cancel Deletion**.
#. In the displayed dialog box, click **OK** to cancel the scheduled deletion.

   -  If a key is created on the KMS console, the status of the key changes to **Disabled** after its scheduled deletion is canceled. For details about how to enable the key, see :ref:`Enabling One or More CMKs <kms_01_0029>`.
   -  If the CMK is created using imported materials, its status becomes **Disabled** after the cancellation. To enable the CMK, see :ref:`Enabling One or More CMKs <kms_01_0029>`.
   -  If the CMK is created using imported materials and no key materials have been imported for it, its status becomes **Pending import** after the cancellation. To use the CMK, perform :ref:`Creating CMKs Using Imported Key Materials <kms_01_0142>`.

   .. note::

      To cancel the deletion of multiple CMKs at a time, select them and click **Cancel Deletion** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
