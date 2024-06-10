:original_name: kms_01_0008.html

.. _kms_01_0008:

Encrypting Data in EVS
======================

-  When purchasing a disk, you can choose **Advanced Settings** > **Encryption** to encrypt the disk using the key provided by KMS. For details, see :ref:`Figure 1 <kms_01_0008__fig1372118163416>`. For more information about EVS, see the *Elastic Volume Service User Guide*.

   .. note::

      Before you use the encryption function, EVS must be granted the permission to access KMS. If you have the right to grant the permission, you can grant the permission directly. If you do not have the permission, contact a user with the security administrator permissions to add the security administrator permission for you. Then, you can grant the permission. For more information about EVS, see the *Elastic Volume Service User Guide*.

   .. _kms_01_0008__fig1372118163416:

   .. figure:: /_static/images/en-us_image_0000001677397941.png
      :alt: **Figure 1** Encrypting data in EVS

      **Figure 1** Encrypting data in EVS

   There are two types of CMKs that can be used:

   -  The default key **evs/default** created by KMS
   -  Custom keys that you create on the KMS console using KMS-generated key materials

-  You can also call EVS APIs to create encrypted EVS disks. For details, see the *Elastic Volume Service API Reference*.
