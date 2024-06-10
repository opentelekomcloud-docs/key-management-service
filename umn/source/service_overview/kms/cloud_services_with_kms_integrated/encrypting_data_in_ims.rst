:original_name: kms_01_0009.html

.. _kms_01_0009:

Encrypting Data in IMS
======================

-  When uploading an image file to Image Management Service (IMS), you can choose to encrypt the image file using a key provided by KMS to protect the file. :ref:`Figure 1 <kms_01_0009__fig144761027111615>` describes details. For details, see the *Image Management Service User Guide*.

   .. _kms_01_0009__fig144761027111615:

   .. figure:: /_static/images/en-us_image_0000001628879300.png
      :alt: **Figure 1** Encrypting data in IMS

      **Figure 1** Encrypting data in IMS

   There are two types of CMKs that can be used:

   -  The default key **ims/default** created by KMS
   -  Custom keys that you create on the KMS console using KMS-generated key materials

-  You can also call IMS APIs to create encrypted image files. For details, see *Image Management Service API Reference*.
