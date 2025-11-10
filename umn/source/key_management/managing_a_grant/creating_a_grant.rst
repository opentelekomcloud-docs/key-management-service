:original_name: kms_01_0029.html

.. _kms_01_0029:

Creating a Grant
================

Scenario
--------

You can create grants for other users to use the custom key. You can create a maximum of 100 grants for a custom key.

The owner of a custom key can create a grant for the custom key on the KMS management console or by making the API calls. A user, who has been granted with the grant creation permission by the owner of the custom key, can create grants for the custom key only by making the API calls.

Prerequisites
-------------

-  You have obtained the user ID of the grantee (user to whom permissions are to be authorized).
-  The desired custom key is in **Enabled** status.

Constraints
-----------

The owner of a custom key can create a grant for the custom key on the KMS console or by calling APIs. The users or accounts who have the grant creation permission assigned by the owner of the custom key can create grants for the custom key only by calling APIs.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the name of the target custom key to view its grant details.


   .. figure:: /_static/images/en-us_image_0000002208263345.png
      :alt: **Figure 1** Grants tab

      **Figure 1** Grants tab

#. Click **Create Grant**. The **Create Grant** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000002172703332.png
      :alt: **Figure 2** Creating a grant

      **Figure 2** Creating a grant

#. In the dialog box that is displayed, enter the ID of the user to be authorized and select permissions to be granted.

   .. important::

      A grantee can perform the authorized operations only by calling the necessary API. For details, see the *Key Management Service API Reference*.

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Parameter             | Description                                                                                                                                                                             | Example Value                    |
      +=======================+=========================================================================================================================================================================================+==================================+
      | Key ID                | ID of a custom key (automatically read by the system)                                                                                                                                   | ``-``                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Grantee               | The user ID of the grantee is required.                                                                                                                                                 | d9a6b2bdaedd4ba586cabe6372d1b312 |
      |                       |                                                                                                                                                                                         |                                  |
      |                       | .. note::                                                                                                                                                                               |                                  |
      |                       |                                                                                                                                                                                         |                                  |
      |                       |    The user IDs are provided by grantees who can obtain their IDs by clicking their portraits and choosing **My Credential** > **User ID**.                                             |                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Granted Operations    | The following permissions can be authorized:                                                                                                                                            | ``-``                            |
      |                       |                                                                                                                                                                                         |                                  |
      |                       | .. note::                                                                                                                                                                               |                                  |
      |                       |                                                                                                                                                                                         |                                  |
      |                       |    -  You can create multiple grants on a custom key to provide different permissions to the same user. The user's permissions on the custom key are the combination of all the grants. |                                  |
      |                       |    -  This parameter cannot be left blank.                                                                                                                                              |                                  |
      |                       |    -  **Create Grant** cannot be selected exclusively.                                                                                                                                  |                                  |
      |                       |                                                                                                                                                                                         |                                  |
      |                       | -  **Create Data Key Without Plaintext**                                                                                                                                                |                                  |
      |                       | -  **Create Data Key**                                                                                                                                                                  |                                  |
      |                       | -  **Encrypt Data Key**                                                                                                                                                                 |                                  |
      |                       | -  **Decrypt Data Key**                                                                                                                                                                 |                                  |
      |                       | -  **Query Key Information**                                                                                                                                                            |                                  |
      |                       | -  **Create Grant**                                                                                                                                                                     |                                  |
      |                       | -  **Retire Grant**                                                                                                                                                                     |                                  |
      |                       |                                                                                                                                                                                         |                                  |
      |                       |    -  A grantee can retire a grant if the grantee does not need that permission.                                                                                                        |                                  |
      |                       |    -  If, before retiring a grant, the grantee has granted the permission to another user, that user's permission will not be affected by the grant retirement.                         |                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+

#. Click **OK**. When message **Grant of key alias created successfully** is displayed in the upper right corner, the grant has been created.

   In the list of grants, you can view the grant ID, grantee ID, granted operation, and creation time of the grant.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
