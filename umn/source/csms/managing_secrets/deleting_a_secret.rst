:original_name: dew_01_8889.html

.. _dew_01_8889:

Deleting a Secret
=================

Before deleting a secret, confirm that it is not in use and will not be used.

Prerequisites
-------------

The secret to be deleted is in **Enabled** state.

Constraints
-----------

-  A secret will not be deleted until its scheduled deletion period expires. You can set the period to a value within the range 7 to 30 days. Before the specified deletion date, you can cancel the deletion if you want to use the secret. If the scheduled deletion period of a secret expires, the secret will be deleted and cannot be restored.
-  If you delete a secret immediately, you can restore it using the secret backup that you have downloaded in advance. Exercise caution when performing this operation.


Deleting a Secret
-----------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. In the row of a secret, click **Delete**.

#. On the displayed page, select a deletion mode. If you want to delete the secret in a specific time, set **Schedule deletion**.


   .. figure:: /_static/images/en-us_image_0000002279551361.png
      :alt: **Figure 1** Setting scheduled deletion

      **Figure 1** Setting scheduled deletion

#. Enter **DELETE** in the confirmation dialog box and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
