:original_name: dew_01_0031.html

.. _dew_01_0031:

Deleting a Key
==============

Before deleting the key, confirm that it is not in use and will not be used.

Prerequisites
-------------

The key to be deleted is in **Enabled**, **Disabled**, or **Pending import** status.

Constraints
-----------

-  A key will not be deleted until its scheduled deletion period expires. You can set the period to a value within the range 7 to 1096 days.

   Before the specified deletion date, you can cancel the deletion if you want to use the CMK. Once the scheduled deletion has taken effect, the CMK will be deleted permanently and you will not be able to decrypt data encrypted by the CMK. Exercise caution when performing this operation.

-  Default keys created by KMS cannot be scheduled for deletion.

Procedure
---------

To schedule the deletion of multiple CMKs at a time, select them and click **Delete** in the upper left corner of the list. The following describes how to delete a single key.

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Key Management Service**.

#. Locate the target key and click **Delete** in the **Operation** column.

#. On the key deletion dialog box, enter the deletion delay time.


   .. figure:: /_static/images/en-us_image_0000002278274229.png
      :alt: **Figure 1** Setting scheduled deletion

      **Figure 1** Setting scheduled deletion

#. Enter **DELETE** in the confirmation dialog box and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002479637892.png
