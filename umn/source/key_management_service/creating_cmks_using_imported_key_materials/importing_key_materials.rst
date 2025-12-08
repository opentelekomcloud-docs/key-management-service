:original_name: dew_01_0089.html

.. _dew_01_0089:

Importing Key Materials
=======================

If you want to use your own key materials instead of the KMS-generated materials, you can use the console to import your key materials to KMS. CMKs created using imported materials and KMS-generated materials are managed together by KMS.

This section describes how to import key materials on the KMS console.

Operation Process
-----------------

+----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Scenario                                     | Procedure                                                                                                                                                                                                                                                                            |
+==============================================+======================================================================================================================================================================================================================================================================================+
| Using existing key materials                 | #. :ref:`Creating a key whose material source is external <dew_01_0089__section1232061165711>`: Create an empty key whose material source is external.                                                                                                                               |
|                                              | #. :ref:`Importing key material (existing key material) <dew_01_0089__section8215105213617>`: Import key material and token to the created empty key.                                                                                                                                |
+----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Downloading key materials by calling APIs    | #. :ref:`Creating a key whose material source is external <dew_01_0089__section1232061165711>`: Create an empty key whose material source is external.                                                                                                                               |
|                                              | #. :ref:`Downloading wrapping key and importing a token (by calling the API) <dew_01_0089__scfd68ea997e74909a825386e20128afc>`: Download the wrapping key and import the token by calling the API.                                                                                   |
|                                              | #. :ref:`Using wrapping key to encrypt key material <dew_01_0089__section167823289366>`: Use HSM or OpenSSL to encrypt wrapping key into key material.                                                                                                                               |
|                                              | #. :ref:`Importing key material (existing key material) <dew_01_0089__section19218511587>`: Import key material and token to the created empty key.                                                                                                                                  |
+----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Downloading key materials on the KMS console | #. :ref:`Creating a key whose material source is external <dew_01_0089__section1232061165711>`: Create an empty key whose material source is external.                                                                                                                               |
|                                              | #. :ref:`Downloading wrapping key and importing the token (from the KMS console) <dew_01_0089__section197084131607>`: Download wrapping key from the KMS console. The import token is automatically guided by the console.                                                           |
|                                              |                                                                                                                                                                                                                                                                                      |
|                                              |    .. important::                                                                                                                                                                                                                                                                    |
|                                              |                                                                                                                                                                                                                                                                                      |
|                                              |       NOTICE:                                                                                                                                                                                                                                                                        |
|                                              |       After downloading wrapping key, do not close or exit the **Import Key Material** dialog box. After the key material is encrypted, you need to perform the :ref:`Import Key Material (Continue to Import Key Material) <dew_01_0089__section1421715592815>` in this dialog box. |
|                                              |                                                                                                                                                                                                                                                                                      |
|                                              | #. :ref:`Using wrapping key to encrypt key material <dew_01_0089__section167823289366>`: Use HSM or OpenSSL to encrypt wrapping key into key material.                                                                                                                               |
|                                              | #. :ref:`Importing Key Material (Continue Importing Key Material) <dew_01_0089__section1421715592815>`: Import the key material to the created empty key.                                                                                                                            |
+----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dew_01_0089__section1232061165711:

Step 1: Creating a Key Using External Materials
-----------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| on the left and choose **Security** > **Key Management Service**.
#. Click **Create Key** in the upper right corner of the page to create an empty key whose **Source** is **External**. For details about more parameters, see :ref:`Step 5 <dew_01_0178__li19889912558>`.

Step 2: Downloading the Wrapping Key and Importing Token
--------------------------------------------------------

The key management function provides two download modes:

-  Download the wrapping key and import token by calling the API.
-  Download the wrapping key from the KMS console. The import token is automatically passed by the console. Therefore, do not close or exit the **Import Key Material** dialog box after the key material is downloaded. Otherwise, the imported token will automatically become invalid.

.. _dew_01_0089__scfd68ea997e74909a825386e20128afc:

Downloading the Wrapping Key By Calling APIs
--------------------------------------------

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

   a. Copy the content of the wrapping key **public_key**, paste it to a .txt file, and save the file as **PublicKey.b64**.

   b. Use OpenSSL to run the following command to perform Base-64 coding on the content of the **PublicKey.b64** file to generate binary data, and save the converted file as **PublicKey.bin**:

      **openssl** **enc** **-d** **-base64** **-A** **-in** **PublicKey.b64** **-out** **PublicKey.bin**

#. Save the import token, copy the content of the **import_token** token, paste it to a .txt file, and save the file as **ImportToken.b64**.

.. _dew_01_0089__section197084131607:

Downloading the Wrapping Key on the KMS Console
-----------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner of the management console and select a region or project.

#. Click |image4| on the left and choose **Security** > **Key Management Service**.

#. In the **Custom Keys** tab, locate the key created by :ref:`Step 1: Creating a Key Using External Materials <dew_01_0089__section1232061165711>` and click **Import Key Material** in the **Operation** column.

#. In the **Download the Import Items** area, select a key wrapping algorithm based on :ref:`Key wrapping algorithm <dew_01_0089__table25919249015>`.


   .. figure:: /_static/images/en-us_image_0000002277965541.png
      :alt: **Figure 1** Obtaining the wrapping key and import token

      **Figure 1** Obtaining the wrapping key and import token

   .. _dew_01_0089__table25919249015:

   .. table:: **Table 1** Key wrapping algorithms

      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
      | Algorithm             | Description                                                        | Configuration                                                                                                  |
      +=======================+====================================================================+================================================================================================================+
      | RSAES_OAEP_SHA_256    | RSA algorithm that uses OAEP and has the **SHA-256** hash function | Select an algorithm based on your HSM functions.                                                               |
      |                       |                                                                    |                                                                                                                |
      |                       |                                                                    | If the HSMs support the **RSAES_OAEP_SHA_256** algorithm, use **RSAES_OAEP_SHA_256** to encrypt key materials. |
      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

#. .. _dew_01_0089__li142446213516:

   Click **Download Key Material** to download the wrapping key file, as shown in :ref:`Figure 2 <dew_01_0089__fig6615246013>`.

   .. _dew_01_0089__fig6615246013:

   .. figure:: /_static/images/en-us_image_0000002141499297.png
      :alt: **Figure 2** Downloading a file

      **Figure 2** Downloading a file

   -  **wrappingKey\_**\ *KeyID* is the wrapping key. It is encoded in binary format and used to encrypt the wrapping key of the key material.
   -  Import token: You do not need to download it. The import wizard automatically transfers the import token. If you close the wizard before completing the import, the token will automatically become invalid.

   .. important::

      The wrapping key expires in 24 hours. If the wrapping key is invalid, download it again.

      The console automatically passes the import token. Therefore, do not close or exit the **Import Key Material** dialog box after the key material is downloaded. Otherwise, the imported token will automatically become invalid.

      After downloading wrapping key, :ref:`use it to encrypt the key material <dew_01_0089__section167823289366>`. Then, import the key material in the **Import Key Material** dialog box. For details, see :ref:`Importing Key Materials <dew_01_0089__section1421715592815>`.

.. _dew_01_0089__section167823289366:

Step 3: Using Wrapping Key to Encrypt Key Materials
---------------------------------------------------

Symmetric and asymmetric key encryption modes generate different key materials.

-  Symmetric key: The key material is **EncryptedKeyMaterial.bin**.
-  Asymmetric key: **EncryptedKeyMaterial.bin** (temporary key material) and **out_rsa_private_key.der** (private key ciphertext)

Symmetric Keys
--------------

-  Method 1: Use the downloaded wrapping key to encrypt key materials on your HSM. For details, see the operation guide of your HSM.
-  Method 2: Use OpenSSL to generate a key material and use the downloaded wrapping key to encrypt the key material.

   .. note::

      If you need to run the **openssl pkeyutl** command, ensure your OpenSSL version is 1.0.2 or later.

   #. To generate a key material for a 256-bit symmetric key, on the agent where OpenSSL has been installed, run the following command to generate the key material and save it as **PlaintextKeyMaterial.bin**:

      -  AES256 symmetric key

         **openssl** **rand** **-out** **PlaintextKeyMaterial.bin** **32**

   #. Use the downloaded wrapping key to encrypt the key material and save the encrypted key material as **EncryptedKeyMaterial.bin**.

      If the wrapping key was downloaded from the console, replace **PublicKey.bin** in the following command with the wrapping key name *wrappingKey_keyID*.

      .. table:: **Table 2** Encrypting the generated key material using the downloaded wrapping key

         +------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Wrapping Key Algorithm | Key Material Encryption                                                                                                                                                                     |
         +========================+=============================================================================================================================================================================================+
         | RSAES_OAEP_SHA_256     | **openssl pkeyutl -in PlaintextKeyMaterial.bin -inkey PublicKey.bin -out EncryptedKeyMaterial.bin -keyform der -pubin -encrypt -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256** |
         +------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Asymmetric Keys
---------------

-  Method 1: Use the downloaded wrapping key to encrypt key materials on your HSM. For details, see the operation guide of your HSM.
-  Method 2: Use OpenSSL to generate a key material and use the downloaded wrapping key to encrypt the key material.

   .. note::

      If you need to run the **openssl pkeyutl** command, ensure your OpenSSL version is 1.0.2 or later.

   #. To generate a key material for a 256-bit symmetric key, on the agent where OpenSSL has been installed, run the following command to generate the key material and save it as **PlaintextKeyMaterial.bin**:

      -  RSA and ECC asymmetric keys

         a. Generate a hexadecimal AES256 key.

            **openssl rand -out 0xPlaintextKeyMaterial.bin -hex 32**

         b. Convert the hexadecimal AES256 key to the binary format.

            **cat 0xPlaintextKeyMaterial.bin \| xxd -r -ps > PlaintextKeyMaterial.bin**

   #. Use the downloaded wrapping key to encrypt the key material and save the encrypted key material as **EncryptedKeyMaterial.bin**.

      If the wrapping key was downloaded from the console, replace **PublicKey.bin** in the following command with the wrapping key name *wrappingKey_keyID*.

      .. table:: **Table 3** Encrypting the generated key material using the downloaded wrapping key

         +------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Wrapping Key Algorithm | Key Material Encryption                                                                                                                                                                     |
         +========================+=============================================================================================================================================================================================+
         | RSAES_OAEP_SHA_256     | **openssl pkeyutl -in PlaintextKeyMaterial.bin -inkey PublicKey.bin -out EncryptedKeyMaterial.bin -keyform der -pubin -encrypt -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256** |
         +------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   #. To import an asymmetric key, generate an asymmetric private key, use the temporary key material (**EncryptedKeyMaterial.bin**) to encrypt the private key, and import the encrypted file as the private key ciphertext.

      -  Take the **RSA4096 algorithm** as an example.

         a. Generate a private key.

            **openssl genrsa -out pkcs1_rsa_private_key.pem 4096**

         b. Convert the format to PKCS8.

            **openssl pkcs8 -topk8 -inform PEM -in pkcs1_rsa_private_key.pem -outform pem -nocrypt -out rsa_private_key.pem**

         c. Convert the PKCS8 format to the DER format.

            **openssl pkcs8 -topk8 -inform PEM -outform DER -in rsa_private_key.pem -out rsa_private_key.der -nocrypt**

         d. Use a temporary key material to encrypt the private key.

            **openssl enc -id-aes256-wrap-pad -K $(cat 0xPlaintextKeyMaterial.bin) -iv A65959A6 -in rsa_private_key.der -out out_rsa_private_key.der**

            .. note::

               By default, the -id-aes256-wrap-pad algorithm is not enabled in OpenSSL. To wrap a key, upgrade OpenSSL to the latest version and patch it first. For details, see FAQs.

.. _dew_01_0089__section8215105213617:

Step 4: Importing Key Materials
-------------------------------

The import method varies depending on the key material download method.

-  If the key material is downloaded by calling the API or the key material already exists, run the :ref:`Importing Existing Key Materials <dew_01_0089__section19218511587>`.
-  To download the key material using the KMS console, run the :ref:`Importing Key Materials <dew_01_0089__section1421715592815>`.

.. _dew_01_0089__section19218511587:

Importing Existing Key Materials
--------------------------------

#. Log in to the management console.

#. Click |image5| in the upper left corner of the management console and select a region or project.

#. Click |image6| on the left and choose **Security** > **Key Management Service**.

#. In the **Custom Keys** tab, locate the key created by :ref:`Step 1: Creating a Key Using External Materials <dew_01_0089__section1232061165711>` and click **Import Key Material** in the **Operation** column.

#. In the **Download the Import Items** area, select a key wrapping algorithm based on :ref:`Key wrapping algorithm <dew_01_0089__dew_01_0089_table25919249015>`.


   .. figure:: /_static/images/en-us_image_0000002277965541.png
      :alt: **Figure 3** Obtaining the wrapping key and import token

      **Figure 3** Obtaining the wrapping key and import token

   .. _dew_01_0089__dew_01_0089_table25919249015:

   .. table:: **Table 4** Key wrapping algorithms

      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
      | Algorithm             | Description                                                        | Configuration                                                                                                  |
      +=======================+====================================================================+================================================================================================================+
      | RSAES_OAEP_SHA_256    | RSA algorithm that uses OAEP and has the **SHA-256** hash function | Select an algorithm based on your HSM functions.                                                               |
      |                       |                                                                    |                                                                                                                |
      |                       |                                                                    | If the HSMs support the **RSAES_OAEP_SHA_256** algorithm, use **RSAES_OAEP_SHA_256** to encrypt key materials. |
      +-----------------------+--------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

#. Click **Use Existing Key Material**. In the **Import Key Material** area, enter **Key Material**.


   .. figure:: /_static/images/en-us_image_0000002243177908.png
      :alt: **Figure 4** Importing key materials

      **Figure 4** Importing key materials

   .. table:: **Table 5** Key material description

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scenario                          | Description                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================+
      | Symmetric key                     | Use the key material encrypted by wrapping key.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | For example, the **EncryptedKeyMaterial.bin** file in :ref:`Step 3: Using Wrapping Key to Encrypt Key Materials <dew_01_0089__section167823289366>`.                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Asymmetric key                    | Use the temporary key material and private key ciphertext encrypted by wrapping key.                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | For example, the temporary key material **EncryptedKeyMaterial.bin** and private key ciphertext **out_rsa_private_key.der** in :ref:`Step 3: Using Wrapping Key to Encrypt Key Materials <dew_01_0089__section167823289366>`. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**. In the **Import Key Token** area, set parameters based on :ref:`Table 6 <dew_01_0089__tf00e7c9f3be04375a6ceb8b65a9b1697>`.

   .. _dew_01_0089__tf00e7c9f3be04375a6ceb8b65a9b1697:

   .. table:: **Table 6** Parameters for importing a key token

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key import token                  | Enter the import token obtained in :ref:`Downloading the Wrapping Key By Calling APIs <dew_01_0089__scfd68ea997e74909a825386e20128afc>`.                                                                     |
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

.. _dew_01_0089__section1421715592815:


Importing Key Materials
-----------------------

#. In the **Import Key Material** dialog box (:ref:`Step 6 <dew_01_0089__li142446213516>`) on the management console, add the **Key Material** file in the **Import Key Material** configuration item.


   .. figure:: /_static/images/en-us_image_0000002243177908.png
      :alt: **Figure 5** Importing key materials

      **Figure 5** Importing key materials

   .. table:: **Table 7** Key material description

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scenario                          | Description                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================+
      | Symmetric key                     | Use the key material encrypted by wrapping key.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | For example, the **EncryptedKeyMaterial.bin** file in :ref:`Step 3: Using Wrapping Key to Encrypt Key Materials <dew_01_0089__section167823289366>`.                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Asymmetric key                    | Use the temporary key material and private key ciphertext encrypted by wrapping key.                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | For example, the temporary key material **EncryptedKeyMaterial.bin** and private key ciphertext **out_rsa_private_key.der** in :ref:`Step 3: Using Wrapping Key to Encrypt Key Materials <dew_01_0089__section167823289366>`. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next** to go to the **Import Key Token** step. Configure the parameters as described in :ref:`Table 8 <dew_01_0089__table254971517361>`.

   .. _dew_01_0089__table254971517361:

   .. table:: **Table 8** Parameters for importing a key token

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Key ID                            | Random ID of a CMK generated during the CMK creation                                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key material expiration mode      | -  **Key material will never expire**: You use this option to specify that key materials will not expire after import.                                                                                       |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  **Key material will expire**: You use this option to specify the expiration time of the key materials. By default, key materials expire in 24 hours after import.                                         |
      |                                   |                                                                                                                                                                                                              |
      |                                   |    After the key material expires, the system automatically deletes the key material within 24 hours. Once the key material is deleted, the key cannot be used and its status changes to **Pending import**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. When the **Key imported successfully** message is displayed in the upper right corner, the materials are imported.

   .. important::

      Key material can be successfully imported when it matches the corresponding key ID.

   Your imported materials are displayed in the list of CMKs. The default status of an imported CMK is **Enabled**.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511514115.png
.. |image3| image:: /_static/images/en-us_image_0000001284811084.png
.. |image4| image:: /_static/images/en-us_image_0000002479477424.png
.. |image5| image:: /_static/images/en-us_image_0000001284811084.png
.. |image6| image:: /_static/images/en-us_image_0000002479637434.png
