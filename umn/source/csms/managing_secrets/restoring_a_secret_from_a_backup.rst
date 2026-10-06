:original_name: dew_01_0338.html

.. _dew_01_0338:

Restoring a Secret from a Backup
================================

DEW allows you to restore a secret from backup.

Prerequisites
-------------

-  The secret backup is downloaded during secret creation.
-  After a secret is restored from backup, the secret ID will be changed.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Click **Restore Secret**, select a backup file, and click **OK**.

   .. caution::

      Only secret backup files smaller than 5 MB can be uploaded.


   .. figure:: /_static/images/en-us_image_0000002279435737.png
      :alt: **Figure 1** Restoring a secret backup

      **Figure 1** Restoring a secret backup

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
