:original_name: dew_01_0178.html

.. _dew_01_0178:

Creating a Key
==============

This section describes how to create a custom key on the KMS console.

Custom keys can be categorized into symmetric keys and asymmetric keys.

Constraints
-----------

-  You can create up to 100 custom keys, excluding default keys.
-  A custom key is created using the AES-256 algorithm and is 256 bit long.
-  Asymmetric keys are created using RSA or ECC algorithms. RSA keys can be used for encryption, decryption, digital signature, and signature verification. ECC keys can be used only for digital signature and signature verification.
-  Aliases of default keys end with **/default**. When choosing aliases for your custom keys, do not use aliases ending with **/default**.
-  KMS does not limit the number of times that a key can be called.

Scenarios
---------

-  Encrypt data in OBS.
-  Encrypt data in EVS.
-  Encrypt data in IMS.
-  Use custom keys to directly encrypt and decrypt small volumes of data.
-  DEK encryption and decryption for user applications
-  Message authentication code generation and verification


Creating a Key
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Key Management Service**.

#. Click **Create Key** in the upper right corner.

#. .. _dew_01_0178__li19889912558:

   Configure the parameters as follows:


   .. figure:: /_static/images/en-us_image_0000002278002189.png
      :alt: **Figure 1** Creating a key

      **Figure 1** Creating a key

   .. table:: **Table 1** Key parameter configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                         |
      +===================================+=====================================================================================================================================================+
      | Name                              | Name of the key you are creating.                                                                                                                   |
      |                                   |                                                                                                                                                     |
      |                                   | .. note::                                                                                                                                           |
      |                                   |                                                                                                                                                     |
      |                                   |    -  You can enter digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/).                                                     |
      |                                   |    -  You can enter up to 255 characters.                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Algorithm                     | Select a key algorithm.                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Usage                             | Key usage. The value cannot be changed after the key is created. The value can be **SIGN_VERIFY**, **ENCRYPT_DECRYPT**, or **GENERATE_VERIFY_MAC**. |
      |                                   |                                                                                                                                                     |
      |                                   | -  For an AES_256 symmetric key, the default value is **ENCRYPT_DECRYPT**.                                                                          |
      |                                   | -  For an HMAC symmetric key, the default value is **GENERATE_VERIFY_MAC**.                                                                         |
      |                                   | -  For RSA asymmetric keys, select **ENCRYPT_DECRYPT** or **SIGN_VERIFY**. The default value is **SIGN_VERIFY**.                                    |
      |                                   | -  For an ECC asymmetric key, the default value is **SIGN_VERIFY**.                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Material Source               | -  Key management                                                                                                                                   |
      |                                   | -  External                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced settings                 | -  Description                                                                                                                                      |
      |                                   |                                                                                                                                                     |
      |                                   |    Description of the key.                                                                                                                          |
      |                                   |                                                                                                                                                     |
      |                                   | -  Tag                                                                                                                                              |
      |                                   |                                                                                                                                                     |
      |                                   |    You can add tags to a secret as you need.                                                                                                        |
      |                                   |                                                                                                                                                     |
      |                                   |    .. note::                                                                                                                                        |
      |                                   |                                                                                                                                                     |
      |                                   |       A maximum of 20 tags can be added for one custom key.                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Related Operations
------------------

-  For details about how to upload objects with server-side encryption, see section "Uploading a File with Server-Side Encryption" in *Object Storage Service (OBS) User Guide*.
-  For details about how to encrypt data on EVS disks, see section "Creating an EVS Disk" in *Elastic Volume Service (EVS) User Guide*.
-  For details about how to encrypt private images, see section "Encrypting an Image" in *Image Management Service (IMS) User Guide*.
-  For details about how to encrypt disks for a database instance in RDS, see section "Purchasing an Instance" in the *Relational Database Service User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511593267.png
