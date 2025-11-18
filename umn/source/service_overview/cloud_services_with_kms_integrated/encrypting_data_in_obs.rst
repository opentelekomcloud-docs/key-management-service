:original_name: dew_01_0007.html

.. _dew_01_0007:

Encrypting Data in OBS
======================

-  When using Object Storage Service (OBS) to upload data with server-side encryption, you can select **SEE-KMS encryption** and use the key provided by KMS to encrypt the files to be uploaded. For details, see :ref:`Figure 1 <dew_01_0007__en-us_topic_0112947554_fig1096125520374>`. For details, see *Object Storage Service Console Operation Guide*.

   .. _dew_01_0007__en-us_topic_0112947554_fig1096125520374:

   .. figure:: /_static/images/en-us_image_0000002207465277.png
      :alt: **Figure 1** Encrypting Data in OBS

      **Figure 1** Encrypting Data in OBS

   There are two types of CMKs that can be used:

   -  The default key **obs/default** created by KMS
   -  Custom keys that you created on the KMS console

-  Alternatively, you can call OBS APIs to upload a file with server-side encryption using KMS-managed keys (SSE-KMS). For details, see .
