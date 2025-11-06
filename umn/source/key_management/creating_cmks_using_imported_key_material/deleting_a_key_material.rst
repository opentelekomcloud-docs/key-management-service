:original_name: kms_01_0020.html

.. _kms_01_0020:

Deleting a Key Material
=======================

Scenario
--------

When importing key material, you can specify the expiration time. After the key material expires, KMS deletes it, and the status of the custom key changes to **Pending import**. You can manually delete the key material as needed. The effect of expiration of the key material is the same as that of manual deletion of the key material.

This section describes how to delete imported key material on the management console.

Constraints
-----------

-  To re-import a deleted key material, ensure the imported material is the same as the deleted one.
-  Data encrypted using a custom key cannot be decrypted if the key material of the custom key was deleted. To decrypt the data, re-import the key material.
-  After the deletion, the key will become unavailable and its status will change to **Pending import**.

Prerequisites
-------------

-  You have imported the key material for a key.
-  The material source of the key is **External**.
-  The key status is **Enabled** or **Disabled**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Locate the target key material and choose **More** > **Delete Key Material** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   After the deletion, the key will become unavailable and its status changes to **Pending import**.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
