:original_name: kms_01_0072.html

.. _kms_01_0072:

Deleting a Key
==============

Scenario
--------

This section describes how to use the management console to schedule the deletion of one or multiple unwanted custom keys.

If deletion is scheduled for a key, the deletion will not take effect immediately. Instead, it will take effect after a waiting period of 7 to 1096 days. Before the specified deletion date, you can cancel the deletion if you want to use the key. Once the scheduled deletion has taken effect, the key will be deleted permanently and you will not be able to decrypt data encrypted by it. Therefore, you are advised to exercise caution when performing this operation.

Before deleting the key, confirm that it is not in use and will not be used.

-  You can configure the SMN notification function to receive notifications when OBS fails to use the key to decrypt data before the deletion date. If you want to use the key again, cancel its deletion on the console. For SMN configuration instructions, see :ref:`Configuring SMN <kms_01_0021>`.
-  You can choose **Storage** > **Elastic Volume Service** to go to the EVS page. In the search bar, select **KMS key ID** and enter the key ID to check whether the key is being used by EVS.
-  You can choose **Computing** > **Image Management Service** to go to the IMS page. Select the **Private Image** tab. In the search bar, select **KMS key ID** and enter the key ID to check whether the key is being used by IMS.
-  You can choose **Storage** > **Scalable File Service** to go to the SFS page. In the search bar, select **KMS key ID** and enter the key ID to check whether the key is being used by SFS.
-  You can choose **Database** > **Relational Database Service** to view the database instance list, and click the name of the target database instance. On the details page of the database instance, check whether the key to be deleted is in use.

.. note::

   Default Master Keys created by KMS cannot be scheduled for deletion.

Prerequisites
-------------

-  The key to be deleted is in **Enabled**, **Disabled**, or **Pending Import** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the row containing the desired key, click **Delete**.


   .. figure:: /_static/images/en-us_image_0000002172809156.png
      :alt: **Figure 1** Scheduling the deletion for a single key

      **Figure 1** Scheduling the deletion for a single key

#. On the key deletion dialog box, enter the deletion delay time.


   .. figure:: /_static/images/en-us_image_0000002172654270.png
      :alt: **Figure 2** Scheduling a deletion time

      **Figure 2** Scheduling a deletion time

#. Click **Yes** to schedule the deletion.

   .. note::

      To delete multiple keys at a time, select them and click **Delete** in the upper left corner of the list.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
