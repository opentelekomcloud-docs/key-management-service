:original_name: kms_01_0139.html

.. _kms_01_0139:

Enabling Key Rotation
=====================

This section describes how to enable rotation for a key on the KMS console.

By default, automatic key rotation is disabled for a custom key. Every time you enable key rotation, KMS automatically rotates custom keys based on the rotation period you set.

Prerequisites
-------------

-  The key is enabled.
-  The **Origin** of the key is **KMS**.
-  Only symmetric keys can be rotated.

Constraints
-----------

-  A disabled custom key is never rotated, even if rotation is enabled for it.

   KMS resumes rotation when this custom key is enabled. If you enable this custom key after one rotation period has passed, KMS will rotate it within 24 hours.

-  Only CMKs can be rotated.

Procedure
---------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

3. Click the alias of the target custom key to view its details.

4. Click the **Rotation Policy** tab. The rotation switch is displayed.

5. Click |image2| to enable key rotation.

6. In the **Enable Rotation Policy** dialog box, set the rotation period and click **OK**.

   -  Set the rotation period (unit: day) to an integer in the range 30 to 365. The default value is **365**.
   -  After the setting takes effect, the new rotation period starts.
   -  Configure the period based on how often a custom key is used. If it is frequently used, configure a short period. Otherwise, set a long one.

      .. note::

         -  A disabled custom key is never rotated, even if rotation is enabled for it.
         -  KMS resumes rotation when this custom key is enabled. If you enable this custom key after one rotation period has passed, KMS will rotate it within 24 hours.
         -  You can click |image3| to change the rotation period. After the period is changed, KMS rotates the key by the new period.

7. Check rotation details, as shown in the following figure.


   .. figure:: /_static/images/en-us_image_0000001678663053.png
      :alt: **Figure 1** Key rotation details

      **Figure 1** Key rotation details

   .. note::

      You can click |image4| to change the rotation period. After the period is changed, KMS rotates the key by the new period.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
.. |image2| image:: /_static/images/en-us_image_0000001348333869.png
.. |image3| image:: /_static/images/en-us_image_0000001295496116.png
.. |image4| image:: /_static/images/en-us_image_0231665754.png
