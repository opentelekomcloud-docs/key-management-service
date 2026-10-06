:original_name: dew_01_9993.html

.. _dew_01_9993:

Creating a Shared Secret
========================

This section describes how to create a secret on the CSMS console.

You can create a secret and store its value in its initial version, which is marked as **SYSCURRENT**.

Constraints
-----------

-  A user can create a maximum of 500 secrets.
-  By default, the default key **csms/default** created by CSMS is used as the encryption key of the current secret. You can also create a user-defined symmetric key and use a user-defined encryption key on the KMS console.

Creating a Secret
-----------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Click **Create Secret**. Configure parameters in the **Create Secret** dialog box, as shown in :ref:`Figure 1 <dew_01_9993__fig6122115715507>`. For details about the parameters, see :ref:`Table 1 <dew_01_9993__table454471191320>`.

   .. _dew_01_9993__fig6122115715507:

   .. figure:: /_static/images/en-us_image_0000002243687008.png
      :alt: **Figure 1** Creating a secret

      **Figure 1** Creating a secret

   .. _dew_01_9993__table454471191320:

   .. table:: **Table 1** Secret parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================+
      | Type                              | Secret type. The default value is **Shared secret**.                                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Secret Name                       | Secret name                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    Only letters, digits, periods (.), hyphens (-), and underscores (_) are allowed.                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | This parameter is provided for enterprise users. If you are an enterprise user and have created an enterprise project, select the required enterprise project from the drop-down list. The default project is **default**. |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    If you have not enabled enterprise management, this parameter will not be displayed.                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Secret Value                      | Secret key/value pair or the plaintext secret to be encrypted                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | KMS Encryption Key                | The following modes are supported:                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | -  **Select from list**: Select this if you want to use the key used or shared by the current account. Select the default key **csms/default** or a custom key created on KMS.                                             |
      |                                   | -  **Enter**: Enter the ID of the authorized key. Enter an encryption key if an authorized key is used. Only symmetric algorithm key IDs are supported. Do not enter an asymmetric key ID.                                 |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    -  CSMS encrypts secret values using the encryption key provided by KMS. When you use the KMS encryption function, KMS creates a default key **csms/default** for you to use.                                           |
      |                                   |    -  For details about how to create a custom key on KMS, see "Creating a Key".                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced settings                 | -  **Associated events**                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    Select an associated event for the secret. You can check information such as secret rotation and version expiration.                                                                                                    |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | -  **Description**                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    Description of a secret                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                            |
      |                                   | -  **Tag**                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    You can add tags to a secret as you need.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |    .. note::                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                            |
      |                                   |       You can add at most 20 tags to a secret.                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**.

#. Click **Next** and confirm the creation information.

#. Click **OK**. In the secret list, you can view the created secrets. The default status of a secret is **Enabled**.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
