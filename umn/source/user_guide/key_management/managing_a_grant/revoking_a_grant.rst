:original_name: kms_01_0031.html

.. _kms_01_0031:

Revoking a Grant
================

Scenario
--------

You can revoke a grant in either of the following scenarios:

-  A grantee does not need the grant. (The grantee can either tell the user who has created the grant to revoke the grant or call the necessary API to revoke the grant directly.)
-  You do not want the grantee to have the grant.

When a grant is revoked, the grantee does not have the corresponding permission anymore. However, if the grantee has created the same grant to another user, permission of that user will not be affected.

This section describes how to revoke a grant.

Prerequisites
-------------

You have created a grant.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Choose **Security** > **Key Management Service** . The key management page is displayed.
#. Click the alias of the desired CMK to view its details.
#. In the row containing the desired grantee, click **Revoke Grant** in the **Operation** column.
#. In the dialog box that is displayed, click **Yes**. When **Grant grant_ID revoked successfully** is displayed in the upper right corner, the grant has been revoked.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
