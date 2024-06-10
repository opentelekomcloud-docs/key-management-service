:original_name: kms_01_0089.html

.. _kms_01_0089:

Importing Key Materials
=======================

If you want to use your own key materials instead of the KMS-generated materials, you can use the console to import your key materials to KMS. CMKs created using imported materials and KMS-generated materials are managed together by KMS.

This section describes how to import key materials on the KMS console.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. Click **Import Key**. The **Import Key** dialog box is displayed.

#. Configure key parameters.


   .. figure:: /_static/images/en-us_image_0000001677751557.png
      :alt: **Figure 1** Creating an empty key

      **Figure 1** Creating an empty key

   -  **Alias** is the alias of the key to be created.

      .. note::

         -  You can enter digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/).
         -  You can enter up to 255 characters.

   -  (Optional) **Description** is the description of the custom key.

      .. note::

         You can enter up to 255 characters.

#. (Optional) Add tags to the custom key as needed, and enter the tag key and tag value.

   .. note::

      -  If a custom key has been created without any tag, you can add a tag to the custom key later if needed. Click the alias of the custom key, choose the **Tags** tab, and click **Add Tag**.
      -  The same tag (including tag key and tag value) can be used for different custom keys. However, under the same custom key, one tag key can have only one tag value.
      -  A maximum of 20 tags can be added for one custom key.
      -  If you want to delete a tag from the tag list when adding multiple tags, you can click **Delete** in the row where the tag to be added is located to delete the tag.

#. Click **security and durability** to understand the security and durability of the imported key.

#. Select **I understand the security and durability of using an imported key**, and create a custom key whose key material is empty.

#. Click **Next** to go to the **Download the Import Items** step. Select a key wrapping algorithm based on :ref:`Table 1 <kms_01_0089__table123192815372>`.


   .. figure:: /_static/images/en-us_image_0000001629072682.png
      :alt: **Figure 2** Obtaining the wrapping key and import token

      **Figure 2** Obtaining the wrapping key and import token

   .. _kms_01_0089__table123192815372:

   .. table:: **Table 1** Key wrapping algorithms

      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
      | Algorithm             | Description                                                        | Configuration                                                                                                  |
      +=======================+====================================================================+================================================================================================================+
      | RSAES_OAEP_SHA_256    | RSA algorithm that uses OAEP and has the **SHA-256** hash function | Select an algorithm based on your HSM functions.                                                               |
      |                       |                                                                    |                                                                                                                |
      |                       |                                                                    | If the HSMs support the **RSAES_OAEP_SHA_256** algorithm, use **RSAES_OAEP_SHA_256** to encrypt key materials. |
      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

   .. note::

      If you stop a key material import process and want to try again, click **Import Key Material** in the row of the required custom key, and import key material in the displayed dialog box.

#. Obtain the wrapping key and import token. If you already have a key material, skip this step.

   a. Obtain the wrapping key and import token.

      -  Method 1: Click **Download and Continue** to download the wrapping key file, as shown in :ref:`Figure 3 <kms_01_0089__fig118341118183611>`.

         .. _kms_01_0089__fig118341118183611:

         .. figure:: /_static/images/en-us_image_0000001542027770.png
            :alt: **Figure 3** Downloaded file

            **Figure 3** Downloaded file

         -  **wrappingKey\_**\ *KeyID* is the wrapping key. It is encoded in binary format and used to encrypt the wrapping key of the key material.
         -  Import token: You do not need to download it. The import wizard automatically transfers the import token. If you close the wizard before completing the import, the token will automatically become invalid.

         .. important::

            The wrapping key expires in 24 hours. If the wrapping key is invalid, download it again.

            The import wizard automatically transfers the import token. If you close the wizard before completing the import, the token will automatically become invalid. To retry import, open the import wizard again.

      -  .. _kms_01_0089__li452117406444:

         Method 2: Obtain the wrapping key and import token by calling APIs.

         #. Call the **get-parameters-for-import** API to obtain the wrapping key and import token.

            -  **public_key**: content of the wrapping key (Base-64 encoding) returned after the API call
            -  **import_token**: content of the import token (Base-64 encoding) returned after the API call

            The following example describes how to obtain the wrapping key and import token of a CMK (ID: **43f1ffd7-18fb-4568-9575-602e009b7ee8**; algorithm: **RSAES_OAEP_SHA_256**).

            -  Example request

               .. code-block::

                  {
                      "key_id": "43f1ffd7-18fb-4568-9575-602e009b7ee8",
                      "wrapping_algorithm":"RSAES_OAEP_SHA_256"
                  }

            -  Example response

               .. code-block::

                  {
                      "key_id": "43f1ffd7-18fb-4568-9575-602e009b7ee8",
                      "public_key":"public key base64 encoded data",
                      "import_token":"import token base64 encoded data",
                      "expiration_time":1501578672
                  }

         #. Save the wrapping key and convert its format. Only the key material encrypted using the converted wrapping key can be imported to the management console.

            #. Copy the content of the wrapping key **public_key**, paste it to a .txt file, and save the file as **PublicKey.b64**.

            #. Use OpenSSL to run the following command to perform Base-64 coding on the content of the **PublicKey.b64** file to generate binary data, and save the converted file as **PublicKey.bin**:

               **openssl** **enc** **-d** **-base64** **-A** **-in** **PublicKey.b64** **-out** **PublicKey.bin**

         #. Save the import token, copy the content of the **import_token** token, paste it to a .txt file, and save the file as **ImportToken.b64**.

   b. Use the wrapping key to encrypt the key material.

      .. note::

         After performing this step, you will obtain either of the following files:

         Symmetric key scenario: **EncryptedKeyMaterial.bin** (key material)

         Asymmetric key scenario: **EncryptedKeyMaterial.bin** (temporary key material) and **out_rsa_private_key.der** (private key ciphertext)

      Method 1: Use the downloaded wrapping key to encrypt key materials on your HSM. For details, see the operation guide of your HSM.

      Method 2: Use OpenSSL to generate a key material and use the downloaded wrapping key to encrypt the key material.

      .. note::

         If you need to run the **openssl pkeyutl** command, ensure your OpenSSL version is 1.0.2 or later.

      #. Generate a key material (256-bit symmetric key) and save it as **PlaintextKeyMaterial.bin**.

         -  If the AES256 symmetric key algorithm is used, run the following command on the client where the OpenSSL tool has been installed:

            **openssl** **rand** **-out** **PlaintextKeyMaterial.bin** **32**

         -  If the RSA and ECC asymmetric key algorithms are used, run the following command on the client where the OpenSSL tool has been installed:

            #. Generate a hexadecimal AES256 key.

               **openssl rand -out 0xPlaintextKeyMaterial.bin -hex 32**

            #. Convert the hexadecimal AES256 key to the binary format.

               **cat 0xPlaintextKeyMaterial.bin \| xxd -r -ps > PlaintextKeyMaterial.bin**

      #. .. _kms_01_0089__li12585410398:

         Use the downloaded wrapping key to encrypt the key material and save the encrypted key material as **EncryptedKeyMaterial.bin**.

         If the wrapping key was downloaded from the console, replace **PublicKey.bin** in the following command with the wrapping key name *wrappingKey_keyID*.

         .. table:: **Table 2** Encrypting the generated key material using the downloaded wrapping key

            +-----------------------------------+------------------------------------------------------------------------+
            | Wrapping Key Algorithm            | Key Material Encryption                                                |
            +===================================+========================================================================+
            | RSAES_OAEP_SHA_256                | **openssl** **pkeyutl**                                                |
            |                                   |                                                                        |
            |                                   | **-in** **PlaintextKeyMaterial.bin**                                   |
            |                                   |                                                                        |
            |                                   | **-inkey** **PublicKey.bin**                                           |
            |                                   |                                                                        |
            |                                   | **-out** **EncryptedKeyMaterial.bin**                                  |
            |                                   |                                                                        |
            |                                   | **-keyform** **der**                                                   |
            |                                   |                                                                        |
            |                                   | **-pubin** **-encrypt**                                                |
            |                                   |                                                                        |
            |                                   | **-pkeyopt** **rsa_padding_mode:oaep** **-pkeyopt rsa_oaep_md:sha256** |
            +-----------------------------------+------------------------------------------------------------------------+

      #. .. _kms_01_0089__li287144863910:

         (Optional) To import an asymmetric key, generate an asymmetric private key, use the temporary key material (**EncryptedKeyMaterial.bin**) to encrypt the private key, and import the encrypted file as the private key ciphertext.

         -  Take the RSA4096 algorithm as an example. Perform the following operations:

            #. Generate a private key.

               **openssl genrsa -out pkcs1_rsa_private_key.pem 4096**

            #. Convert the format to PKCS8.

               **openssl pkcs8 -topk8 -inform PEM -in pkcs1_rsa_private_key.pem -outform pem -nocrypt -out rsa_private_key.pem**

            #. Convert the PKCS8 format to the DER format.

               **openssl pkcs8 -topk8 -inform PEM -outform DER -in rsa_private_key.pem -out rsa_private_key.der -nocrypt**

            #. Use a temporary key material to encrypt the private key.

               **openssl enc -id-aes256-wrap-pad -K $(cat 0xPlaintextKeyMaterial.bin) -iv A65959A6 -in rsa_private_key.der -out out_rsa_private_key.der**

               .. note::

                  By default, the -id-aes256-wrap-pad algorithm is not enabled in OpenSSL. To wrap a key, upgrade OpenSSL to the latest version and patch it first. For details, see FAQs.

#.  The **Import Key Material** page is displayed.

   .. table:: **Table 3** Parameters for importing key materials (for symmetric keys)

      +-----------------------------------+--------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                            |
      +===================================+========================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------+
      | Key material                      | Import a key material.                                                                                 |
      |                                   |                                                                                                        |
      |                                   | For example, use the **EncryptedKeyMaterial.bin** file in :ref:`10.b.ii <kms_01_0089__li12585410398>`. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Parameters for importing key materials (for asymmetric keys)

      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                |
      +===================================+============================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Temporary key material            | Import a temporary key material.                                                                           |
      |                                   |                                                                                                            |
      |                                   | For example, select the **EncryptedKeyMaterial.bin** file in :ref:`10.b.ii <kms_01_0089__li12585410398>`.  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Private key ciphertext            | Select private key ciphertext.                                                                             |
      |                                   |                                                                                                            |
      |                                   | For example, select the **out_rsa_private_key.der** file in :ref:`10.b.iii <kms_01_0089__li287144863910>`. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+

#. Click **Next** to go to the **Import Key Token** step. Configure the parameters as described in :ref:`Table 5 <kms_01_0089__tf00e7c9f3be04375a6ceb8b65a9b1697>`.

   .. _kms_01_0089__tf00e7c9f3be04375a6ceb8b65a9b1697:

   .. table:: **Table 5** Parameters for importing a key token

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key import token                  | Select the import token obtained via API in :ref:`12.b <kms_01_0089__li452117406444>`.                                                                                                                       |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key material expiration mode      | -  **Key material will never expire**: You use this option to specify that key materials will not expire after import.                                                                                       |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  **Key material will expire**: You use this option to specify the expiration time of the key materials. By default, key materials expire in 24 hours after import.                                         |
      |                                   |                                                                                                                                                                                                              |
      |                                   |    After the key material expires, the system automatically deletes the key material within 24 hours. Once the key material is deleted, the key cannot be used and its status changes to **Pending import**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. When the **Key imported successfully** message is displayed in the upper right corner, the materials are imported.

   .. important::

      Key materials can be successfully imported when they match the corresponding CMK ID and token.

   Your imported materials are displayed in the list of CMKs. The default status of an imported CMK is **Enabled**.

.. |image1| image:: /_static/images/en-us_image_0000001677425609.png
.. |image2| image:: /_static/images/en-us_image_0000001295227514.png
