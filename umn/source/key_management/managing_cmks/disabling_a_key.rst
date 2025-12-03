:original_name: kms_01_0035.html

.. _kms_01_0035:

Disabling a Key
===============

Scenario
--------

This section describes how to use the management console to disable one or multiple custom keys, thereby protecting data in urgent cases.

After being disabled, a custom key cannot be used to encrypt or decrypt any data. Before using a disabled key to encrypt or decrypt data, you must enable it by following instructions in :ref:`Enabling a Key <kms_01_0034>`.

.. note::

   Default keys created by KMS cannot be disabled.

Prerequisites
-------------

The key you want to disable is in **Enabled** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the row containing the desired key, click **Disable**.


   .. figure:: /_static/images/en-us_image_0000002172804952.png
      :alt: **Figure 1** Disabling a single key

      **Figure 1** Disabling a single key

#. In the dialog box that is displayed, select **I understand the impact of disabling keys** and click **OK**.

   .. note::

      To disable multiple keys at a time, select them and click **Disable** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
