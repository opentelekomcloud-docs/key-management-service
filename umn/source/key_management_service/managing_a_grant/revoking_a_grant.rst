:original_name: dew_01_0098.html

.. _dew_01_0098:

Revoking a Grant
================

You can revoke a grant on the KMS console in either of the following scenarios:

-  A grantee does not need the custom key grant. (The grantee can either tell the user who has created the grant to revoke the grant or call the necessary API to revoke the grant directly.)
-  You do not want the grantee to have the grant.

When a grant is revoked, the grantee does not have the corresponding permission anymore. However, if the grantee has created the same grant to another user, permission of that user will not be affected.

This section describes how to revoke a grant on the KMS console.

Prerequisites
-------------

You have created a grant.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Key Management Service**.

#. Click the alias of the target custom key to view its details.

#. In the **Grants** tab, locate the target grant and click **Revoke Grant** in the **Operation** column.

#. Enter **DELETE** in the confirmation dialog box and click **OK**.

   In the displayed dialog box, click **OK**. If **Grant grant ID revoked successfully** is displayed in the upper right corner, the grant has been revoked.

   .. note::

      You can call the API to verify that the key grant has been revoked. For example, if the grant to create a data key is revoked for a user, an error will be reported when the user calls the API to create a data key.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002479481472.png
