:original_name: kms_01_0107.html

.. _kms_01_0107:

How Do I Use the Online Tool to Encrypt or Decrypt Small Volumes of Data?
=========================================================================

You can use the online tool to encrypt or decrypt data in the following procedures:

Encrypting Data
---------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the name of the target custom key to access the key details page. Click the **Tool** tab.

#. Click **Encrypt**. In the text box on the left, enter the data to be encrypted.


   .. figure:: /_static/images/en-us_image_0000002255480681.png
      :alt: **Figure 1** Encrypting data

      **Figure 1** Encrypting data

#. Click **Execute**. The data encryption result is displayed in the text box on the right.

   .. note::

      -  The key you clicked is used for encryption.
      -  To clear your input, click **Clear**.
      -  To copy the encrypted data, click **Copy to Clipboard**. You can then paste and save it to a local file.

Decrypting Data
---------------

#. Log in to the management console.

#. Click |image2| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the alias of an enabled key (excepting Default Master Keys) to access its details page.

#. Click the **Tool** tab.

#. Click **Decrypt**. In the text box on the left, enter the data to be decrypted.

   .. note::

      -  The online tool automatically identifies the key used for data encryption, and uses it to decrypt data.
      -  If the key has been deleted, the decryption will fail.


   .. figure:: /_static/images/en-us_image_0000002220522126.png
      :alt: **Figure 2** Decrypting data

      **Figure 2** Decrypting data

#. Click **Execute**. The data decryption result is displayed in plaintext in the text box on the right.

   .. note::

      To copy the decrypted data, click **Copy to Clipboard**. You can then paste and save it to a local file.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0237800345.png
