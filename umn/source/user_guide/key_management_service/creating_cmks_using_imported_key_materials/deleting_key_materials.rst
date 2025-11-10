:original_name: kms_01_0090.html

.. _kms_01_0090:

Deleting Key Materials
======================

When importing key materials, you can specify their expiration time. After the key material expires, KMS deletes it, and the status of the custom key changes to **Pending import**. You can manually delete the key materials as needed. The effect of expiration of the key material is the same as that of manual deletion of the key material.

This section describes how to delete imported key materials on the KMS console.

.. note::

   -  To re-import a deleted key material, ensure the imported material is the same as the deleted one.
   -  Data encrypted using a CMK cannot be decrypted if the key material of the custom key was deleted. To decrypt the data, re-import the key material.

Prerequisites
-------------

-  You have imported key materials for a CMK.
-  The material source of the CMK is **External**.
-  The CMK status is **Enabled** or **Disabled**.

Constraints
-----------

-  To re-import a deleted key material, ensure the imported material is the same as the deleted one.
-  Data encrypted using a CMK cannot be decrypted if the key material of the custom key was deleted. To decrypt the data, re-import the key material.
-  After the deletion, the CMK will become unavailable and its status will change to **Pending import**.
-  The key materials of asymmetric keys cannot be directly deleted. To delete them, perform the instructions in :ref:`Deleting One or More CMKs <kms_01_0031>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. In the row containing the target CMK, click **Delete Key Material**.

#. In the displayed dialog box, click **OK**. When **Key material deleted successfully** is displayed in the upper right corner, the key materials are successfully deleted.

   After the deletion, the CMK will become unavailable and its status changes to **Pending import**.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
