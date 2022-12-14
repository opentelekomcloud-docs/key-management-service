:original_name: kms_01_0094.html

.. _kms_01_0094:

Context
=======

Security risks exist when a DEK is extensively and repeatedly used. For security purposes, you can configure KMS to create new key materials for the CMK.

New key materials can be created in two methods:

-  Manual key rotation

   Create a CMK on the KMS management console to replace the original CMK.

   .. note::

      If cloud services (such as OBS) use a CMK to encrypt and decrypt data, you need to create a new CMK on the KMS management console and replace the original one used for KMS encryption on OBS Console.

-  Automatic key rotation

   Enable rotation for an existing CMK so that KMS automatically generates new key material for the CMK.

   Key rotation only changes the key material of a CMK. The CMK's attributes (such as ID, alias, description, and permissions settings) remain unchanged.

   The key rotation function enables KMS to automatically rotate CMKs according to the specified rotation interval (365 days by default). For a CMK with the key rotation function enabled, a new version is generated upon each rotation. See :ref:`Figure 1 <kms_01_0094__fig9231144353>` for details.

   .. _kms_01_0094__fig9231144353:

   .. figure:: /_static/images/en-us_image_0205545064.png
      :alt: **Figure 1** Working principle of key rotation

      **Figure 1** Working principle of key rotation

   KMS retains all versions associated of the CMK, so that you can decrypt any ciphertext encrypted using the CMK.

   -  KMS uses the latest version of the CMK to encrypt data.
   -  KMS uses the same version of the CMK to decrypt data as that used to encrypt the data.

   .. table:: **Table 1** Key rotation modes

      +--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Type                       | Support for Key Rotation                                                                                                                                                                                                                                                                                                                                                    |
      +================================+=============================================================================================================================================================================================================================================================================================================================================================================+
      | Default Master Key             | Keys cannot be rotated.                                                                                                                                                                                                                                                                                                                                                     |
      +--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Imported CMK                   | Keys can only be rotated manually.                                                                                                                                                                                                                                                                                                                                          |
      +--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Disabled CMK                   | KMS does not rotate disabled CMKs and keeps their rotation status unchanged. After a CMK is enabled, if the backup CMK has been used for longer than the rotation period, KMS will immediately rotate keys. If the backup CMK has been used for shorter than the rotation period, KMS will implement the original rotation plan.                                            |
      +--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | CMK in pending deletion status | KMS does not rotate CMKs in pending deletion status. After you cancel the deletion of a CMK, the previous key rotation status will be restored. If the backup CMK has been used for longer than the rotation period, KMS will immediately rotate keys. If the backup CMK has been used for shorter than the rotation period, KMS will implement the original rotation plan. |
      +--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
