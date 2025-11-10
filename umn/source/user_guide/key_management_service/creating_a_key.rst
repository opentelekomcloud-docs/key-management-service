:original_name: kms_01_0178.html

.. _kms_01_0178:

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

-  Encrypt data in OBS
-  Encrypt data in EVS
-  Encrypt data in IMS
-  Use custom keys to directly encrypt and decrypt small volumes of data.
-  DEK encryption and decryption for user applications


Creating a Key
--------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. Click **Create Bucket** in the upper right corner.

#. Configure parameters in the **Create Key** dialog box.


   .. figure:: /_static/images/en-us_image_0000001677425385.png
      :alt: **Figure 1** Creating a key

      **Figure 1** Creating a key

   -  **Alias** is the alias of the key to be created.

      .. note::

         -  You can enter digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/).
         -  You can enter up to 255 characters.

   -  **Key Algorithm**: Select a key algorithm. For more information, see :ref:`Table 1 <kms_01_0178__table0624027274>`.

      .. _kms_01_0178__table0624027274:

      .. table:: **Table 1** Key algorithms supported by KMS

         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
         | Key Type       | Algorithm Type | Key Specifications | Description                        | Usage                                                                       |
         +================+================+====================+====================================+=============================================================================+
         | Symmetric key  | AES            | -  AES_256         | AES symmetric key                  | Encrypts and decrypts a small amount of data or data keys.                  |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
         | Asymmetric key | RSA            | -  RSA_2048        | RSA asymmetric password            | Encrypts and decrypts a small amount of data or creates digital signatures. |
         |                |                | -  RSA_3072        |                                    |                                                                             |
         |                |                | -  RSA_4096        |                                    |                                                                             |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+
         |                | ECC            | -  EC_P256         | Elliptic curve recommended by NIST | Digital signature                                                           |
         |                |                | -  EC_P384         |                                    |                                                                             |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------+

   -  **Usage**: Select **SIGN_VERIFY** or **ENCRYPT_DECRYPT**.

      -  For an AES_256 symmetric key, the default value is **ENCRYPT_DECRYPT**.
      -  For RSA asymmetric keys, select **ENCRYPT_DECRYPT** or **SIGN_VERIFY**. The default value is **SIGN_VERIFY**.
      -  For an ECC asymmetric key, the default value is **SIGN_VERIFY**.

      .. note::

         The key usage can only be configured during key creation and cannot be modified afterwards.

   -  (Optional) **Description** is the description of the custom key.

      .. note::

         You can enter up to 255 characters.

#. (Optional) Add tags to the custom key as needed, and enter the tag key and tag value.

   .. note::

      -  After creating a CMK, you can click the alias of the CMK to go to the CMK details page and add a tag to the CMK.
      -  The same tag (including tag key and tag value) can be used for different custom keys. However, under the same custom key, one tag key can have only one tag value.
      -  A maximum of 20 tags can be added for one custom key.
      -  To delete a tag, click **Delete** next to it.

#. Click **OK**. A message is displayed in the upper right corner of the page, indicating that the key is created successfully.

   In the key list, you can view the created keys. The default status of a key is **Enabled**.

Related Operations
------------------

-  For details about how to upload objects with server-side encryption, see section "Uploading a File with Server-Side Encryption" in *Object Storage Service User Guide*.
-  For details about how to encrypt data on EVS disks, see section "Creating an EVS Disk" in *Elastic Volume Service User Guide*.
-  For details about how to encrypt private images, see section "Encrypting an Image" in *Image Management Service User Guide*.
-  For details about how to encrypt disks for a database instance in RDS, see section "Purchasing an Instance" in the *Relational Database Service User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001677425609.png
.. |image2| image:: /_static/images/en-us_image_0000001295227514.png
