:original_name: kms_01_0194.html

.. _kms_01_0194:

Creating a Key
==============

Scenario
--------

This section describes how to create a custom key on the KMS management console. You can create up to 100 custom keys, excluding default keys.

CMKs can be used for:

-  Server-side encryption on OBS
-  Encryption of data on EVS disks
-  Encryption of private images on IMS
-  File system encryption on SFS
-  Disk encryption for database instances in RDS
-  DEK encryption and decryption for user applications

Constraints
-----------

-  You can create up to 100 custom keys, excluding default keys.
-  Names of default keys end with **/default**. When configuring names for your custom keys, the value cannot end with **/default**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click **Create Key** in the upper right corner. In the displayed dialog box, enter the alias, names, tags, and description of the key.


   .. figure:: /_static/images/en-us_image_0000002172246184.png
      :alt: **Figure 1** Creating a Key

      **Figure 1** Creating a Key

   -  **Name**: Name of the key to be created
   -  **Key Algorithm**: Key algorithm supported by KMS. See the following table for details.

      .. table:: **Table 1** Key algorithms supported by KMS

         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Key Type       | Algorithm Type | Key Specifications | Description                        | Application Scenario                                                                                                                                                                                                  |
         +================+================+====================+====================================+=======================================================================================================================================================================================================================+
         | Symmetric key  | AES            | AES_256            | AES symmetric key                  | -  Data encryption and decryption                                                                                                                                                                                     |
         |                |                |                    |                                    | -  DEKs encryption and decryption                                                                                                                                                                                     |
         |                |                |                    |                                    |                                                                                                                                                                                                                       |
         |                |                |                    |                                    |    .. note::                                                                                                                                                                                                          |
         |                |                |                    |                                    |                                                                                                                                                                                                                       |
         |                |                |                    |                                    |       You can encrypt and decrypt a small amount of data using the the online tool on the console.                                                                                                                    |
         |                |                |                    |                                    |                                                                                                                                                                                                                       |
         |                |                |                    |                                    |       You need to call APIs to encrypt and decrypt a large amount of data.                                                                                                                                            |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Digest key     | SHA            | -  HMAC_256        | Digest key                         | -  Data tampering prevention                                                                                                                                                                                          |
         |                |                | -  HMAC_384        |                                    | -  Data integrity verification                                                                                                                                                                                        |
         |                |                | -  HMAC_512        |                                    |                                                                                                                                                                                                                       |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Asymmetric key | RSA            | -  RSA_2048        | RSA asymmetric password            | -  Digital signature and signature verification                                                                                                                                                                       |
         |                |                | -  RSA_3072        |                                    | -  Data encryption and decryption                                                                                                                                                                                     |
         |                |                | -  RSA_4096        |                                    |                                                                                                                                                                                                                       |
         |                |                |                    |                                    |    .. note::                                                                                                                                                                                                          |
         |                |                |                    |                                    |                                                                                                                                                                                                                       |
         |                |                |                    |                                    |       Asymmetric keys are applicable to signature and signature verification scenarios. Asymmetric keys are not efficient enough for data encryption. Symmetric keys are suitable for encrypting and decrypting data. |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                | ECC            | -  EC_P256         | Elliptic curve recommended by NIST | Digital signature and signature verification                                                                                                                                                                          |
         |                |                | -  EC_P384         |                                    |                                                                                                                                                                                                                       |
         +----------------+----------------+--------------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  **Usage**: Select **SIGN_VERIFY**, **GENERATE_VERIFY_MAC**, or **ENCRYPT_DECRYPT**.

      -  For an AES_256 symmetric key, the default value is **ENCRYPT_DECRYPT**.
      -  For an HMAC symmetric key, the default value is **GENERATE_VERIFY_MAC**.
      -  For RSA asymmetric keys, select **ENCRYPT_DECRYPT** or **SIGN_VERIFY**. The default value is **SIGN_VERIFY**.
      -  For an ECC asymmetric key, the default value is **SIGN_VERIFY**.

      .. note::

         The key usage can only be configured during key creation and cannot be modified afterwards.

   -  (Optional) **Description** is the description of the custom key.
   -  (Optional) **Tags**: Add tags to the custom key as needed, and enter the tag key and tag value.

      .. note::

         -  If a custom key has been created without any tag, you can add a tag to the custom key later as necessary. Click the name of the custom key. The page with key details is displayed. Then you can add tags to the custom key.
         -  The same tag (including tag key and tag value) can be used for different custom keys. However, under the same custom key, one tag key can have only one tag value.
         -  A maximum of 20 tags can be added for one custom key.
         -  If you want to delete a tag to be added when adding multiple tags, you can click **Delete** in the row where the tag to be added is located to delete the tag.

#. Click **OK**.

   In the custom key list, you can view created custom keys. The default status of a custom key is **Enabled**.

Related Operations
------------------

-  For details about how to upload objects with server-side encryption, see section **Uploading a File with Server-Side Encryption** in the *Object Storage Service User Guide*.
-  For details about how to encrypt data on EVS disks, see section **Creating an EVS Disk** in the *Elastic Volume Service User Guide*.
-  For details about how to encrypt private images, see section **Encrypting an Image** in the *Image Management Service User Guide*.
-  For details about how to encrypt the file system on SFS, see section **Creating a File System** in the *Scalable File Service User Guide*.
-  For details about how to encrypt disks for a database instance in RDS, see section **Creating an RDS MySQL DB Instance** in the *Relational Database Service User Guide*.
-  For details about how to create a DEK and a plaintext-free DEK, see sections "Creating a DEK" and "Creating a Plaintext-Free DEK" in .
-  For details about how to encrypt and decrypt a DEK for a user application, see sections "Encrypting a DEK" and "Decrypting a DEK" in .

.. |image1| image:: /_static/images/en-us_image_0237800345.png
