:original_name: kms_01_0139.html

.. _kms_01_0139:

Enabling Key Rotation
=====================

Scenario
--------

This section describes how to enable rotation for a key on the KMS console.

By default, automatic key rotation is disabled for a CMK. Every time you enable key rotation, KMS automatically rotates CMKs based on the rotation period you set.

Prerequisites
-------------

-  The key is enabled.
-  The **Origin** of the key is **KMS**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the name of the target custom key to view its details.

#. Click **Rotation Policy**. The dialog box is displayed, as shown in :ref:`Figure 1 <kms_01_0139__fig69311343123217>`.

   .. _kms_01_0139__fig69311343123217:

   .. figure:: /_static/images/en-us_image_0000002208177921.png
      :alt: **Figure 1** Key rotation

      **Figure 1** Key rotation

#. Click |image2| to enable key rotation.

#. In the **Enable Rotation Policy** dialog box, set the rotation period and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002208180117.png
      :alt: **Figure 2** Setting the rotation period

      **Figure 2** Setting the rotation period

   Set the rotation period (unit: day) to an integer in the range 30 to 365. The default value is **365**.

   After the setting takes effect, the new rotation period starts.

   Configure the period based on how often a custom key is used. If it is frequently used, configure a short period; otherwise, set a long one.

#. After rotation is enabled, the rotation details will be displayed, as shown in :ref:`Figure 3 <kms_01_0139__fig1995485414369>`.

   .. _kms_01_0139__fig1995485414369:

   .. figure:: /_static/images/en-us_image_0000002208255689.png
      :alt: **Figure 3** Key rotation details

      **Figure 3** Key rotation details

   After rotation is enabled, the key will be rotated based on your set period.

   .. note::

      -  A disabled custom key is never rotated, even if rotation is enabled for it.
      -  KMS resumes rotation when this custom key is enabled. If you enable this custom key after one rotation period has passed, KMS will rotate it within 24 hours.
      -  You can click |image3| to change the rotation period. After the period is changed, KMS rotates the key by the new period.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0000002208253509.png
.. |image3| image:: /_static/images/en-us_image_0249630192.png
