:original_name: kms_01_0036.html

.. _kms_01_0036:

Canceling the Scheduled Deletion of One or Multiple CMKs
========================================================

Scenario
--------

This section describes how to use the management console to cancel the scheduled deletion of one or multiple CMKs prior to deletion execution.

Prerequisites
-------------

The CMK for which you want to cancel the scheduled deletion is in **Pending deletion** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the row containing the desired CMK, click **Cancel Deletion**.


   .. figure:: /_static/images/en-us_image_0129272144.png
      :alt: **Figure 1** Canceling the scheduled deletion of one CMK

      **Figure 1** Canceling the scheduled deletion of one CMK

#. In the displayed dialog box, click **Yes** to cancel the scheduled deletion for the CMK.

   -  If the CMK is created using KMS generated material, its status becomes **Disabled** after the cancelation. To enable the CMK, see :ref:`Enabling One or Multiple CMKs <kms_01_0034>`.
   -  If the CMK is created using imported material, its status becomes **Disabled** after the cancelation. To enable the CMK, see :ref:`Enabling One or Multiple CMKs <kms_01_0034>`.
   -  If the CMK is created using imported material and no key material has been imported for it, its status becomes **Pending import** after the cancelation. To use the CMK, perform :ref:`Creating CMKs Using Imported Key Material <kms_01_0019>`.

   .. note::

      To cancel the deletion of multiple CMKs at a time, select them and click **Cancel Deletion** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
