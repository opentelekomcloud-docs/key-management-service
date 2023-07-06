:original_name: kms_01_0055.html

.. _kms_01_0055:

Importing a Key Material
========================

Scenario
--------

If you want to use your own key material instead of the KMS-generated material, you can use the console to import your key material to KMS. CMKs created using imported material and KMS-generated material are managed together by KMS.

This section describes how to import key material through KMS Console.

.. note::

   -  A CMK with imported material works in the same way as one using KMS-generated material, that is, you enable and disable them as well as schedule their deletion and cancel their scheduled deletion in the same way.
   -  You can only import 256-bit symmetric keys.

Prerequisites
-------------

-  You have prepared the key material to be imported.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the upper right corner, click **Import Key**.

#. In the **Import Key** dialog box, set the alias and description of the key.


   .. figure:: /_static/images/en-us_image_0129101904.png
      :alt: **Figure 1** Creating a CMK

      **Figure 1** Creating a CMK

   -  **Alias** is the alias of the key to be created.

      .. note::

         -  You can enter digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/).
         -  You can enter up to 255 characters.

   -  (Optional) **Description** is the description of the custom key.
   -  (Optional) Add tags as needed, and enter the tag key and tag value.

      .. note::

         -  When a CMK has been created without any tag, you can add a tag to the CMK later as necessary. Click the alias of the CMK. The page with key details is displayed. Then you can add tags to the CMK.
         -  The same tag (including tag key and tag value) can be used for different CMKs. However, under the same CMK, one tag key can have only one tag value.
         -  A maximum of 10 tags can be added for one CMK.
         -  If you want to delete a tag to be added when adding multiple tags, you can click **Delete** in the row where the tag to be added is located to delete the tag.

#. Click **security and durability** to read and confirm information regarding the security and durability of the imported key.

#. Select **I understand the security and durability of using an imported key**, and create a CMK whose key material is empty.

#. Click **Next** to go to the **Download the Import Items** step. Select a key-wrapping algorithm according to :ref:`Table 1 <kms_01_0055__t7d6edba5e4dc4db1976cc2675499f0f0>`.


   .. figure:: /_static/images/en-us_image_0115888859.png
      :alt: **Figure 2** Obtaining the wrapping key and import token

      **Figure 2** Obtaining the wrapping key and import token

   .. _kms_01_0055__t7d6edba5e4dc4db1976cc2675499f0f0:

   .. table:: **Table 1** Key wrapping algorithms

      +-----------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | Algorithm             | Description                                                                                                         | Configuration                                                                                                          |
      +=======================+=====================================================================================================================+========================================================================================================================+
      | RSAES_OAEP_SHA_256    | RSA encryption algorithm that uses OAEP and has the **SHA-256** hash function                                       | Choose an algorithm from the drop-down list box.                                                                       |
      |                       |                                                                                                                     |                                                                                                                        |
      |                       |                                                                                                                     | a. If the HSMs support the **RSAES_OAEP_SHA_256** algorithm, use **RSAES_OAEP_SHA_256** to encrypt the key material.   |
      |                       |                                                                                                                     | b. If the HSMs do not support OAEP, use **RSAES_PKCS1_V1_5** to encrypt the key material.                              |
      |                       |                                                                                                                     |                                                                                                                        |
      |                       |                                                                                                                     | .. important::                                                                                                         |
      |                       |                                                                                                                     |                                                                                                                        |
      |                       |                                                                                                                     |    NOTICE:                                                                                                             |
      |                       |                                                                                                                     |    The **RSAES_OAEP_SHA_1** encryption algorithm is no longer secure. Exercise caution when performing this operation. |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | RSAES_PKCS1_V1_5      | RSA encryption algorithm (v1.5) of Public-Key Cryptography Standards number 1 (PKCS #1)                             |                                                                                                                        |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | RSAES_OAEP_SHA_1      | RSA encryption algorithm that uses Optimal Asymmetric Encryption Padding (OAEP) and has the **SHA-1** hash function |                                                                                                                        |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If you stop a key material import process and want to try again, click **Import Key Material** in the row of the required CMK, and import key material in the dialog box that is displayed.

#. .. _kms_01_0055__lc2cb9f68855a42a089a31c63f7975d25:

   Click **Download**. The following files are downloaded: **wrappingKey**, **importToken**, and **README**. These are displayed in :ref:`Figure 3 <kms_01_0055__f269bed6da96f473e84cc76bc0c12fcd5>`.

   .. _kms_01_0055__f269bed6da96f473e84cc76bc0c12fcd5:

   .. figure:: /_static/images/en-us_image_0112947083.png
      :alt: **Figure 3** Downloaded files

      **Figure 3** Downloaded files

   -  **wrappingKey\_\ CMK ID\ \_\ download time** is a wrapping key used to encrypt the key material.
   -  **importToken\_\ CMK ID\ \_\ download time** is an import token used to import key material to KMS.
   -  **README\_\ CMK ID\ \_\ download time** is a description file recording information such as a CMK's serial number, wrapping algorithm, wrapping key name, token file name, and the expiration time of the token file and wrapping key.

      .. important::

         The wrapping key and import token expire within 24 hours of creation. If they have expired, download them again.

   Alternatively, you can obtain the wrapping key and import token by calling the API.

   a. Call the **get-parameters-for-import** API to obtain the wrapping key and import token.

      The following example describes how to obtain the wrapping key and import token of a CMK (ID: **43f1ffd7-18fb-4568-9575-602e009b7ee8**; encryption algorithm: **RSAES_PKCS1_V1_5**).

      **public_key**: The content of the wrapping key (Base-64 encoding) returned after calling the API

      **import_token**: Content of the import token (Base-64 encoding) returned after calling the API

      -  Request example

         .. code-block::

            {
                "key_id": "43f1ffd7-18fb-4568-9575-602e009b7ee8",
                "wrapping_algorithm":"RSAES_PKCS1_V1_5"
            }

      -  Response example:

         .. code-block::

            {
                "key_id": "43f1ffd7-18fb-4568-9575-602e009b7ee8",
                "public_key":"public key base64 encoded data",
                "import_token":"import token base64 encoded data",
                "expiration_time":1501578672
            }

   b. Save the wrapping key, and convert its format according to the following procedure. Only the key material that is encrypted using the converted wrapping key can be imported to the management console.

      #. Copy the content of the wrapping key **public_key**, save it to the **.txt** file as **PublicKey.b64**.

      #. Run the following command to convert the Base-64 coding of the **PublicKey.b64** file to binary data, and save the converted file as **PublicKey.bin**:

         **openssl** **enc** **-d** **-base64** **-A** **-in** **PublicKey.b64** **-out** **PublicKey.bin**

   c. Save the import token, copy the content of the **import_token** token, paste it to a **.txt** file, and save the file as **ImportToken.b64**.

#. You use the downloaded **wrappingKey** file to encrypt the key material to be imported.

   -  Method 1: Use the downloaded wrapping key to encrypt the key material on your HSM. For details, see the operation guide of your HSM.

   -  Method 2: Use OpenSSL to encrypt a key material and use the downloaded wrapping key to encrypt the key material.

      .. note::

         If you need to run the **openssl pkeyutl** command, the OpenSSL version must be 1.0.2 or later.

      The following example describes how to use the downloaded wrapping key to encrypt the generated key material (256-bit symmetric key). The procedure is as follows:

      a. Run the following command to generate the key material (256-bit symmetric key) and save the generated key material as **PlaintextKeyMaterial.bin**:

         **openssl** **rand** **-out** **PlaintextKeyMaterial.bin** **32**

      b. Use the downloaded wrapping key to encrypt the key material and save the encrypted key material as **EncryptedKeyMaterial.bin**.

         Replace **PublicKey.bin** in the command with the name of the wrapping key *wrappingKey_key ID_download time* downloaded in :ref:`9 <kms_01_0055__lc2cb9f68855a42a089a31c63f7975d25>`.

         .. table:: **Table 2** Encrypting the generated key material using the downloaded wrapping key

            +-----------------------------------+--------------------------------------------------------------------------+
            | Wrapping Key Algorithm            | Key Materials Encryption                                                 |
            +===================================+==========================================================================+
            | RSAES_OAEP_SHA_256                | **openssl** **pkeyutl**                                                  |
            |                                   |                                                                          |
            |                                   | **-in** **PlaintextKeyMaterial.bin**                                     |
            |                                   |                                                                          |
            |                                   | **-inkey** **PublicKey.bin**                                             |
            |                                   |                                                                          |
            |                                   | **-out** **EncryptedKeyMaterial.bin**                                    |
            |                                   |                                                                          |
            |                                   | **-keyform** **der**                                                     |
            |                                   |                                                                          |
            |                                   | **-pubin** **-encrypt**                                                  |
            |                                   |                                                                          |
            |                                   | **-pkeyopt** **rsa_padding_mode:oaep** **-pkeyopt rsa_oaep_md:sha256**   |
            +-----------------------------------+--------------------------------------------------------------------------+
            | RSAES_PKCS1_V1_5                  | **openssl** **rsautl** **-encrypt**                                      |
            |                                   |                                                                          |
            |                                   | **-in** **PlaintextKeyMaterial.bin**                                     |
            |                                   |                                                                          |
            |                                   | **-pkcs**                                                                |
            |                                   |                                                                          |
            |                                   | **-inkey** **PublicKey.bin**                                             |
            |                                   |                                                                          |
            |                                   | **-keyform** **der**                                                     |
            |                                   |                                                                          |
            |                                   | **-pubin**                                                               |
            |                                   |                                                                          |
            |                                   | **-out** **EncryptedKeyMaterial.bin**                                    |
            +-----------------------------------+--------------------------------------------------------------------------+
            | RSAES_OAEP_SHA_1                  | **openssl** **pkeyutl**                                                  |
            |                                   |                                                                          |
            |                                   | **-in** **PlaintextKeyMaterial.bin**                                     |
            |                                   |                                                                          |
            |                                   | **-inkey** **PublicKey.bin**                                             |
            |                                   |                                                                          |
            |                                   | **-out** **EncryptedKeyMaterial.bin**                                    |
            |                                   |                                                                          |
            |                                   | **-keyform** **der**                                                     |
            |                                   |                                                                          |
            |                                   | **-pubin** **-encrypt**                                                  |
            |                                   |                                                                          |
            |                                   | **-pkeyopt** **rsa_padding_mode:oaep** **-pkeyopt** **rsa_oaep_md:sha1** |
            +-----------------------------------+--------------------------------------------------------------------------+

#. Click **Next**. Go to the **Import Key Material** step. Configure the parameters as described in :ref:`Table 3 <kms_01_0055__ta53da73a8072468e9b86d7fa3a6fd53e>`.


   .. figure:: /_static/images/en-us_image_0115888849.png
      :alt: **Figure 4** Importing key material

      **Figure 4** Importing key material

   .. _kms_01_0055__ta53da73a8072468e9b86d7fa3a6fd53e:

   .. table:: **Table 3** Parameters for importing key material

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                            |
      +===================================+========================================================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Key material                      | a. Use the key material encrypted by the **wrappingKey** file downloaded in :ref:`9 <kms_01_0055__lc2cb9f68855a42a089a31c63f7975d25>`. |
      |                                   | b. Click **Import** to import the key material.                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next** to go to the **Import Key Token** step. Configure the parameters as described in :ref:`Table 4 <kms_01_0055__t1963e04e0ac24f3e8feb0387fa53c844>`.


   .. figure:: /_static/images/en-us_image_0129539391.png
      :alt: **Figure 5** Importing a key token

      **Figure 5** Importing a key token

   .. _kms_01_0055__t1963e04e0ac24f3e8feb0387fa53c844:

   .. table:: **Table 4** Parameters for importing a key token

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                   |
      +===================================+===============================================================================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Token                             | Select the **importToken** downloaded in :ref:`9 <kms_01_0055__lc2cb9f68855a42a089a31c63f7975d25>`.                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key material expiration mode      | -  **Key material will never expire**: This option specifies that key material will not expire after import.                                                  |
      |                                   |                                                                                                                                                               |
      |                                   | -  **Key material expires on**: This option specifies the expiration time of the key material. By default, the key material expires in 24 hours after import. |
      |                                   |                                                                                                                                                               |
      |                                   |    When the key material expires, KMS will delete them in 24 hours, making the CMK unusable and the CMK status **Pending import**.                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   .. important::

      Key material can be successfully imported when it matches the corresponding CMK ID and token.

   Your imported material is displayed in the list of CMKs. The default status of an imported CMK is **Enabled**.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
