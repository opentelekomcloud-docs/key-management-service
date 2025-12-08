:original_name: dew_01_0053.html

.. _dew_01_0053:

How Do Cloud Services Use KMS to Encrypt Data?
==============================================

Services (such as OBS, IMS, EVS, SFS, DDS, and RDS) use the envelope encryption method provided by KMS to protect data.

.. note::

   Envelope encryption is the practice of encrypting data with a DEK and then encrypting the DEK with a root key that you can fully manage. In this case, CMKs are not required for encryption or decryption.

Envelope Encryption and Decryption Principles
---------------------------------------------

-  :ref:`Figure 1 <dew_01_0053__dew_01_0006_fig1265115271176>` illustrates the process for encrypting a local file.

   .. _dew_01_0053__dew_01_0006_fig1265115271176:

   .. figure:: /_static/images/en-us_image_0232858228.png
      :alt: **Figure 1** Encrypting a local file

      **Figure 1** Encrypting a local file

   The procedure is as follows:

   #. Create a CMK on KMS.
   #. Call the **create-datakey** API of KMS to create a DEK. Then you get a plaintext DEK and a ciphertext DEK. The ciphertext DEK is generated when you use a CMK to encrypt the plaintext DEK.
   #. Use the plaintext DEK to encrypt the file. A ciphertext file is generated.
   #. Save the ciphertext DEK and the ciphertext file together in a persistent storage device or a storage service.

-  :ref:`Figure 2 <dew_01_0053__dew_01_0006_fig133981165810>` illustrates the process for decrypting a local file.

   .. _dew_01_0053__dew_01_0006_fig133981165810:

   .. figure:: /_static/images/en-us_image_0232858842.png
      :alt: **Figure 2** Decrypting a local file

      **Figure 2** Decrypting a local file

   The procedure is as follows:

   #. Obtain the ciphertext DEK and file from the persistent storage device or the storage service.

   #. Call the **decrypt-datakey** API of KMS and use the corresponding CMK (the one used for encrypting the DEK) to decrypt the ciphertext DEK. Then you get the plaintext DEK.

      If the CMK is deleted, the decryption fails. Therefore, properly keep your CMKs.

   #. Use the plaintext DEK to decrypt the ciphertext file.
