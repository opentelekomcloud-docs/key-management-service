:original_name: kms_01_0098.html

.. _kms_01_0098:

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
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.
#. Click the alias of the target custom key to view its details.
#. In the row of a grantee, click **Revoke Grant**.
#. In the dialog box that is displayed, click **OK**. If **Grant grant ID revoked successfully** is displayed in the upper right corner, the grant has been revoked.

   .. note::

      You can call the API to verify that the key grant has been revoked. For details about how to use APIs, see *Key Management Service API Reference*.

      For example, if the grant to create a data key is revoked for a user, an error will be reported when the user calls the API to create a data key.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
