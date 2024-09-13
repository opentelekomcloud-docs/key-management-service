:original_name: kms_01_0007.html

.. _kms_01_0007:

Encrypting Data in OBS
======================

-  When using Object Storage Service (OBS) to upload data with server-side encryption, you can select **KMS encryption** and use the key provided by KMS to encrypt the files to be uploaded. For details, see :ref:`Figure 1 <kms_01_0007__fig1881817208298>`. For more information, see *Object Storage Service User Guide*.

   .. _kms_01_0007__fig1881817208298:

   .. figure:: /_static/images/en-us_image_0000001628743570.png
      :alt: **Figure 1** OBS server-side encryption

      **Figure 1** OBS server-side encryption

   There are two types of CMKs that can be used:

   -  The default key **obs/default** created by KMS
   -  Custom keys that you created on the KMS console

-  Alternatively, you can call OBS APIs to upload a file with server-side encryption using KMS-managed keys (SSE-KMS). For details, see the .
