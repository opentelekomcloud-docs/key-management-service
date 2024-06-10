:original_name: kms_01_0030.html

.. _kms_01_0030:

Disabling One or More CMKs
==========================

This section describes how to use the KMS console to disable one or more custom keys, thereby protecting data in urgent cases.

After being disabled, a custom key cannot be used to encrypt or decrypt any data. Before using a disabled CMK to encrypt or decrypt data, you must enable it by following instructions in :ref:`Enabling One or More CMKs <kms_01_0029>`.

Prerequisites
-------------

The CMK you want to disable is in **Enabled** status.

Constraints
-----------

-  Default keys created by KMS cannot be disabled.
-  A disabled CMK is still billable. It will stop incurring charges if it is deleted.

Procedure
---------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.
#. In the row containing the target CMK, click **Disable**.
#. In the displayed dialog box, select **I understand the impact of disabling keys**, and click **OK**.

   .. note::

      To disable multiple CMKs at a time, select them and click **Disable** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
