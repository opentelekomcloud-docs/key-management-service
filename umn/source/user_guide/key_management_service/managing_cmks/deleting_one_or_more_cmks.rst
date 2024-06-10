:original_name: kms_01_0031.html

.. _kms_01_0031:

Deleting One or More CMKs
=========================

Before deleting the CMK, confirm that it is not in use and will not be used.

Prerequisites
-------------

-  The key to be deleted is in **Enabled**, **Disabled**, or **Pending import** status.

Constraints
-----------

-  A key will not be deleted until its scheduled deletion period expires. You can set the period to a value within the range 7 to 1096 days.

   Before the specified deletion date, you can cancel the deletion if you want to use the CMK. Once the scheduled deletion has taken effect, the CMK will be deleted permanently and you will not be able to decrypt data encrypted by the CMK. Exercise caution when performing this operation.

-  Default keys created by KMS cannot be scheduled for deletion.

Procedure
---------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.
#. In the row containing the target CMK, click **Delete** in the **Operation** column.
#. On the key deletion dialog box, enter the deletion delay time.

   .. note::

      -  A key will not be deleted until its scheduled deletion period expires. You can set the period to a value within the range 7 to 1096 days. Before the specified deletion date, you can cancel the deletion if you want to use the CMK.

.. note::

   To schedule the deletion of multiple CMKs at a time, select them and click **Delete** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
