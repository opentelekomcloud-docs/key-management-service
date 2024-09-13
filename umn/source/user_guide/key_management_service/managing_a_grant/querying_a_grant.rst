:original_name: kms_01_0097.html

.. _kms_01_0097:

Querying a Grant
================

You can view the details about a custom key grant on the KMS console, such as the grant ID, grantee user ID, granted operation, and creation time.

Prerequisites
-------------

You have created a grant.

Procedure
---------

#. Log in to the management console.

#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. Click the alias of the target custom key to view its details.

#. Click **Grant** to view the grant information of the current custom key. :ref:`Table 1 <kms_01_0097__t0484dc5b4d9e4d86a61df05bffcaecf3>` describes the parameters.

   .. _kms_01_0097__t0484dc5b4d9e4d86a61df05bffcaecf3:

   .. table:: **Table 1** Parameter description

      +--------------------+-----------------------------------------------------------------------------------+
      | Parameter          | Description                                                                       |
      +====================+===================================================================================+
      | Grant ID           | Randomly generated unique identification of a grant                               |
      +--------------------+-----------------------------------------------------------------------------------+
      | Granted To         | Whether permissions are granted to a user or account.                             |
      +--------------------+-----------------------------------------------------------------------------------+
      | Grantee ID         | ID of the authorized user or account.                                             |
      +--------------------+-----------------------------------------------------------------------------------+
      | Granted Operations | Authorized operations (such as **Create Data Key**) on the custom key             |
      +--------------------+-----------------------------------------------------------------------------------+
      | Created            | Time when the grant is created                                                    |
      +--------------------+-----------------------------------------------------------------------------------+
      | Operation          | Operations that can be performed on a grant. For example, you can revoke a grant. |
      +--------------------+-----------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
