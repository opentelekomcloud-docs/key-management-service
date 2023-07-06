:original_name: kms_01_0020.html

.. _kms_01_0020:

Deleting a Key Material
=======================

Scenario
--------

When importing key material, you can specify the expiration time. After the key material expires, KMS deletes it, and the status of the CMK changes to **Pending import**. You can manually delete the key material as needed. The effect of expiration of the key material is the same as that of manual deletion of the key material.

This section describes how to delete imported key material on the management console.

.. note::

   -  After the key material is deleted, if you need to re-import the key material, the key material to be imported must be the same as that has been deleted.
   -  After the same key material is re-imported, you can use the CMK to decrypt all data encrypted using this key before deletion.
   -  After the deletion, the CMK will become unavailable and its status will change to **Pending import**.

Prerequisites
-------------

-  You have imported the key material for a CMK.
-  The material source of the CMK is **External**.
-  The CMK status is **Enabled** or **Disabled**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the row containing the desired CMK, click **Delete Key Material**.

#. In the dialog box that is displayed, click **OK**.

   After the deletion, the CMK will become unavailable and its status changes to **Pending import**.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
