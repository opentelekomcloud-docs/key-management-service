:original_name: kms_01_0095.html

.. _kms_01_0095:

Disabling Key Rotation
======================

Scenario
--------

This section describes how to disable rotation for a key on the KMS console.

Prerequisites
-------------

-  You have obtained an account and its password for logging in to the management console.
-  The CMK is in **Enabled** status.
-  The **Origin** of the CMK is **KMS**.
-  Key rotation has been enabled.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. Click the alias of the desired CMK to view its details.

#. Click **Rotation Policy**. The dialog box is displayed, as shown in :ref:`Figure 1 <kms_01_0095__fig68513241314>`.

   .. _kms_01_0095__fig68513241314:

   .. figure:: /_static/images/en-us_image_0249629213.png
      :alt: **Figure 1** CMK rotation details

      **Figure 1** CMK rotation details

#. Click |image2| to disable key rotation.

#. In the displayed **Disable Rotation Policy** dialog box, click **Yes**.


   .. figure:: /_static/images/en-us_image_0249631818.png
      :alt: **Figure 2** Disabling key rotation

      **Figure 2** Disabling key rotation

#. Check the rotation status, as shown in :ref:`Figure 3 <kms_01_0095__fig1580712501294>`.

   .. _kms_01_0095__fig1580712501294:

   .. figure:: /_static/images/en-us_image_0250541308.png
      :alt: **Figure 3** Key rotation

      **Figure 3** Key rotation

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0249631830.png
