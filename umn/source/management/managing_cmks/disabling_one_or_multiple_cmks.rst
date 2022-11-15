:original_name: kms_01_0035.html

.. _kms_01_0035:

Disabling One or Multiple CMKs
==============================

Scenario
--------

This section describes how to use the management console to disable one or multiple CMKs, thereby protecting data in urgent cases.

After being disabled, a CMK cannot be used to encrypt or decrypt any data. Before using a disabled CMK to encrypt or decrypt data, you must enable it by following instructions in :ref:`Enabling One or Multiple CMKs <kms_01_0034>`.

.. note::

   Default Master Keys created by KMS cannot be disabled.

Prerequisites
-------------

-  You have obtained an account and its password for logging in to the management console.
-  The CMK you want to disable is in **Enabled** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. In the row containing the desired CMK, click **Disable**.


   .. figure:: /_static/images/en-us_image_0129271653.png
      :alt: **Figure 1** Disabling one CMK

      **Figure 1** Disabling one CMK

.. |image1| image:: /_static/images/en-us_image_0237800345.png
