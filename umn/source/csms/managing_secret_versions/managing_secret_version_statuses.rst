:original_name: dew_01_8881.html

.. _dew_01_8881:

Managing Secret Version Statuses
================================

This section describes how to add, change, and delete secret version statuses.

Secret values are encrypted and stored in secret versions. A version can have multiple statuses. Versions without any statuses are regarded as deprecated and can be automatically deleted by CSMS.

Constraints
-----------

-  The initial version is marked by the **SYSCURRENT** status tag.
-  You can mark a version with a tag created in the service or a custom tag. A version can have multiple status tags, but a status tag can be used for only one version. For example, if you add the status tag used by version A to version B, the tag will be moved from version A to version B.
-  A secret can have up to 12 version statuses. A status can be used for only one version.
-  **SYSCURRENT** and **SYSPREVIOUS** are preconfigured statuses and cannot be deleted.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Click a secret name to go to the details page.

#. In the **Version List** area, click **Manage Status** in the **Operation** column.

#. In the **Manage Status** dialog box, add, change, or delete the status of a secret version.


   .. figure:: /_static/images/en-us_image_0000002244548524.png
      :alt: **Figure 1** Managing statuses

      **Figure 1** Managing statuses

   -  Adding a version status

      In the **Manage Status** dialog box, click **Add** and enter a status name. Click **OK**.

      .. note::

         A secret can have up to 12 version statuses. A status can be used for only one version.

   -  Updating the version status

      In the **Manage Status** dialog box, click **Change** and select an existing version status. Click **OK**.

   -  Deleting the version status

      In the **Manage Status** dialog box, click **Delete** and select a version status. Click **OK**.

      .. note::

         **SYSCURRENT** and **SYSPREVIOUS** are preconfigured statuses and cannot be deleted.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
