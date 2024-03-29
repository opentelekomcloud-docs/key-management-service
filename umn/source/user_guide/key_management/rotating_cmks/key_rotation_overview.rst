:original_name: kms_01_0094.html

.. _kms_01_0094:

Key Rotation Overview
=====================

Purpose of Key Rotation
-----------------------

Keys that are widely or repeatedly used are insecure. To enhance the security of encryption keys, you are advised to periodically rotate keys and change their key materials.

The purposes of key rotation are:

-  To reduce the amount of data encrypted by each key.

   A key will be insecure if it is used to encrypt a huge number of data. The amount of data encrypted a key refers to the total number of bytes or messages encrypted using the key.

-  To enhance the capability of responding to security events.

   In your initial system security design, you shall design the key rotation function and use it for routine O&M, so that it will be at hand when an emergency occurs.

-  To enhance the data isolation capability.

   The ciphertext data generated before and after key rotation will be isolated. You can identify the impact scope of a security event based on the key involved and take actions accordingly.

Key Rotation Methods
--------------------

You can use either of the following key rotation methods:

-  Manual key rotation

   Replace the key in use with a new key. For example, if key A is in use, you can create key B using a new encryption material, and replace key A with key B. This achieves the same outcome as changing the key material of key A.

   Take OBS as an example. To manually rotate a key, create a new custom key on the KMS console. Replace the old custom key with the new one on the OBS console.


   .. figure:: /_static/images/en-us_image_0000001357411985.png
      :alt: **Figure 1** Manual key rotation

      **Figure 1** Manual key rotation

-  Automatic key rotation

   KMS automatically rotates keys based on the configured rotation period (365 days by default). The system automatically generates a new key to replace the key in use. Automatic key rotation only changes the key material of a CMK. The logical attributes of the key will not change, including its key ID, alias, description, and permissions.

   Automatic key rotation has the following characteristics:

   #. Enable rotation for an existing custom key. KMS will automatically generate new key materials for the custom key.
   #. Data is not re-encrypted in an automatic key rotation. The DEK generated using the CMK is not automatically rotated, and data that has been encrypted using the CMK will not be encrypted again. If a DEK has been leaked, automatic rotation cannot contain the impact of the leakage.


   .. figure:: /_static/images/en-us_image_0000001357372181.png
      :alt: **Figure 2** Key rotation

      **Figure 2** Key rotation

.. note::

   KMS retains all versions of a custom key, so that you can decrypt any ciphertext encrypted using the custom key.

   -  KMS uses the latest version of the custom key to encrypt data.
   -  When decrypting data, KMS uses the custom key version that was used to encrypt the data.

Rotation Modes
--------------

.. table:: **Table 1** Key rotation modes

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key Type                          | Rotation Mode                                                                                                                                                                                                                                                                                              |
   +===================================+============================================================================================================================================================================================================================================================================================================+
   | Default master key                | Cannot be rotated.                                                                                                                                                                                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | User-defined key (imported CMK)   | Can only be manually rotated.                                                                                                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                                                                            |
   |                                   | For more information about user-defined keys, see :ref:`CMK Overview <kms_01_0054__en-us_topic_0112947572_s3f753595a83247f2893dd5dd1ddc46e5>`.                                                                                                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Symmetric key                     | Can be automatically or manually rotated.                                                                                                                                                                                                                                                                  |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disabled CMK                      | Disabled CMKs are not rotated. KMS keeps their rotation status unchanged. After a CMK is enabled, if it has been used for longer than the rotation period, KMS will immediately rotate keys. If the CMK has been used for shorter than the rotation period, KMS will implement the original rotation plan. |
   |                                   |                                                                                                                                                                                                                                                                                                            |
   |                                   | For more information, see :ref:`Disabling One or More CMKs <kms_01_0035>`.                                                                                                                                                                                                                                 |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CMKs in pending deletion state    | Disabled CMKs are not rotated. KMS keeps their rotation status unchanged. After a CMK is enabled, if it has been used for longer than the rotation period, KMS will immediately rotate keys. If the CMK has been used for shorter than the rotation period, KMS will implement the original rotation plan. |
   |                                   |                                                                                                                                                                                                                                                                                                            |
   |                                   | For more information, see :ref:`Scheduling the Deletion of One or More Keys <kms_01_0072>`.                                                                                                                                                                                                                |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   You can check the rotation details on the **Rotation Policy** page, including the last rotation time and number of rotations.
