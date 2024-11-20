:original_name: kms_01_0022.html

.. _kms_01_0022:

Using the Online Tool to Encrypt and Decrypt Small-Size Data
============================================================

This section describes how to use the online tool to encrypt or decrypt small-size data (4 KB or smaller) on the KMS console.

Prerequisites
-------------

The custom key is in **Enabled** status.

Constraints
-----------

-  Default keys cannot be used to encrypt or decrypt such data with the tool.
-  Asymmetric keys cannot be used to encrypt or decrypt such data with the tool.
-  You can call an API to use a default key to encrypt or decrypt small volumes of data. For details, see the *Key Management Service API Reference*.
-  Use the current CMK to encrypt the data.
-  Exercise caution when you delete a CMK. The online tool cannot decrypt data if the CMK used for encryption has been deleted.

Encrypting Data
---------------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

3. Click **Encrypt**. In the text box on the left, enter the data to be encrypted, as shown in :ref:`Figure 1 <kms_01_0022__fig61927028183617>`.

   .. _kms_01_0022__fig61927028183617:

   .. figure:: /_static/images/en-us_image_0000001629601212.png
      :alt: **Figure 1** Encrypting data

      **Figure 1** Encrypting data

4. Click **Execute**. Ciphertext of the data is displayed in the text box on the right.

   .. note::

      -  Use the current CMK to encrypt the data.
      -  You can click **Clear** to clear the entered data.
      -  You can click **Copy to Clipboard** to copy the ciphertext and save it in a local file.

Decrypting Data
---------------

#. Log in to the management console.

2. You can click any non-default key in **Enabled** status to go to the encryption and decryption page of the online tool.

3. Click **Decrypt**. In the text box on the left, enter the data to be decrypted. For details, see :ref:`Figure 2 <kms_01_0022__fig1586514341014>`.

   .. note::

      -  The tool will identify the original encryption CMK and use it to decrypt the data.
      -  If the key has been deleted, the decryption will fail.

   .. _kms_01_0022__fig1586514341014:

   .. figure:: /_static/images/en-us_image_0000001629122164.png
      :alt: **Figure 2** Decrypting data

      **Figure 2** Decrypting data

4. Click **Execute**. Plaintext of the data is displayed in the text box on the right.

   .. note::

      -  You can click **Copy to Clipboard** to copy the plaintext and save it in a local file.

      -  Enter the plaintext on the console, the text will be encoded to Base64 format before encryption.

         The decryption result returned via API will be in Base64 format. Perform Base64 decoding to obtain the plaintext entered on the console.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
