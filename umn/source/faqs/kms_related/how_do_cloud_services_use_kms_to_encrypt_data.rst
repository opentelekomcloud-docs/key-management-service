:original_name: kms_01_0053.html

.. _kms_01_0053:

How Do Cloud Services Use KMS to Encrypt Data?
==============================================

Services (such as OBS, IMS, EVS, SFS, DDS, and RDS) use the envelope encryption method provided by KMS to protect data.

.. note::

   Envelope encryption is an encryption method that enables DEKs to be stored, transmitted, and used in "envelopes" of CMKs. As a result, CMKs do not directly encrypt and decrypt data.

When users download the data from the cloud, the cloud service uses the CMK specified by KMS to decrypt the ciphertext DEK, use the decrypted DEK to decrypt data, and then provide the decrypted data for users to download.
