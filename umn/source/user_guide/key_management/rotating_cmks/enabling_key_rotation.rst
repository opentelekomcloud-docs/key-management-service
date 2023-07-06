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

-  The CMK is in **Enabled** status.
-  The **Origin** of the CMK is **KMS**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the alias of the desired CMK to view its details.

#. Click **Rotation Policy**.


   .. figure:: /_static/images/en-us_image_0250541308.png
      :alt: **Figure 1** Key rotation

      **Figure 1** Key rotation

#. Click |image2| to enable key rotation.

#. In the **Enable Rotation Policy** dialog box, set the rotation period and click **OK**.


   .. figure:: /_static/images/en-us_image_0250401356.png
      :alt: **Figure 2** Setting the rotation period

      **Figure 2** Setting the rotation period

   Set the rotation period (unit: day) to an integer in the range 30 to 365. The default value is **365**.

   After the setting takes effect, the new rotation period starts.

   If the CMK is frequently used, you are advised to set a short rotation period for it; otherwise, set a long one.

#. After rotation is enabled, the rotation details will be displayed, as shown in :ref:`Figure 3 <kms_01_0139__fig68513241314>`.

   .. _kms_01_0139__fig68513241314:

   .. figure:: /_static/images/en-us_image_0249629213.png
      :alt: **Figure 3** CMK rotation details

      **Figure 3** CMK rotation details

   After rotation is enabled, the CMK will be rotated based on your set period.

   .. note::

      -  KMS does not rotate a disabled CMK for which rotation has been enabled.
      -  KMS rotates it when it is enabled again. If it has been longer than the rotation period since the CMK was rotated last time, KMS will rotate the CMK within 24 hours.
      -  You can click |image3| to change the rotation period. After the period is changed, KMS rotates the CMK based on the new period, which starts from the day when the change takes effect.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0249628591.png
.. |image3| image:: /_static/images/en-us_image_0249630192.png
