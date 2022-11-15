:original_name: kms_01_0016.html

.. _kms_01_0016:

Related Services
================

OBS
---

KMS provides central management and control capabilities of CMKs for Object Storage Service (OBS). It is used for server-side encryption with KMS-managed keys (SSE-KMS) function of OBS.

EVS
---

KMS provides central management and control capabilities of CMKs for Elastic Volume Service (EVS). It is applied to the encryption function of EVS.

IMS
---

KMS provides central management and control capabilities of CMKs for Image Management Service (IMS). It is applied to the private image encryption function of IMS.

SFS
---

KMS provides central management and control capabilities of CMKs for Scalable File Service (SFS). It is applied to the file system encryption function of SFS.

RDS
---

KMS provides central management and control capabilities of CMKs for Relational Database Service (RDS). It is applied to the disk encryption of database instances in RDS.

CTS
---

Cloud Trace Service (CTS) provides you with a history of KMS operations. After enabling CTS, you can view all generated traces to review and audit performed KMS operations. For details, see the *Cloud Trace Service User Guide*.

.. table:: **Table 1** KMS operations supported by CTS

   +-------------------------------------------+---------------+-------------------------------+
   | Operation                                 | Resource Type | Trace Name                    |
   +===========================================+===============+===============================+
   | Creating a CMK                            | cmk           | createKey                     |
   +-------------------------------------------+---------------+-------------------------------+
   | Creating a DEK                            | cmk           | createDataKey                 |
   +-------------------------------------------+---------------+-------------------------------+
   | Creating a plaintext-free DEK             | cmk           | createDataKeyWithoutPlaintext |
   +-------------------------------------------+---------------+-------------------------------+
   | Enabling a CMK                            | cmk           | enableKey                     |
   +-------------------------------------------+---------------+-------------------------------+
   | Disabling a CMK                           | cmk           | disableKey                    |
   +-------------------------------------------+---------------+-------------------------------+
   | Encrypting a DEK                          | cmk           | encryptDataKey                |
   +-------------------------------------------+---------------+-------------------------------+
   | Decrypting a DEK                          | cmk           | decryptDataKey                |
   +-------------------------------------------+---------------+-------------------------------+
   | Scheduling the deletion of a CMK          | cmk           | scheduleKeyDeletion           |
   +-------------------------------------------+---------------+-------------------------------+
   | Canceling the scheduled deletion of a CMK | cmk           | cancelKeyDeletion             |
   +-------------------------------------------+---------------+-------------------------------+
   | Generating random numbers                 | rng           | genRandom                     |
   +-------------------------------------------+---------------+-------------------------------+
   | Changing the alias of a CMK               | cmk           | updateKeyAlias                |
   +-------------------------------------------+---------------+-------------------------------+
   | Changing the description of a CMK         | cmk           | updateKeyDescription          |
   +-------------------------------------------+---------------+-------------------------------+
   | Prompting risks about CMK deletion        | cmk           | deleteKeyRiskTips             |
   +-------------------------------------------+---------------+-------------------------------+
   | Importing key material                    | cmk           | importKeyMaterial             |
   +-------------------------------------------+---------------+-------------------------------+
   | Deleting key material                     | cmk           | deleteImportedKeyMaterial     |
   +-------------------------------------------+---------------+-------------------------------+
   | Creating a grant                          | cmk           | createGrant                   |
   +-------------------------------------------+---------------+-------------------------------+
   | Retiring a grant                          | cmk           | retireGrant                   |
   +-------------------------------------------+---------------+-------------------------------+
   | Revoking a grant                          | cmk           | revokeGrant                   |
   +-------------------------------------------+---------------+-------------------------------+
   | Adding a tag                              | cmk           | createKeyTag                  |
   +-------------------------------------------+---------------+-------------------------------+
   | Deleting a tag                            | cmk           | deleteKeyTag                  |
   +-------------------------------------------+---------------+-------------------------------+
   | Batch creating tags                       | cmk           | batchCreateKeyTags            |
   +-------------------------------------------+---------------+-------------------------------+
   | Batch deleting tags                       | cmk           | batchDeleteKeyTags            |
   +-------------------------------------------+---------------+-------------------------------+
   | Enabling key rotation                     | cmk           | enableKeyRotation             |
   +-------------------------------------------+---------------+-------------------------------+
   | Modifying the rotation interval           | cmk           | updateKeyRotationInterval     |
   +-------------------------------------------+---------------+-------------------------------+
   | Disabling key rotation                    | cmk           | disableKeyRotation            |
   +-------------------------------------------+---------------+-------------------------------+

IAM
---

Identity and Access Management (IAM) provides the permission management function for KMS. Only users who have KMS Administrator permissions can use KMS. To apply for KMS Administrator permissions, contact a user with Security Administrator permissions. For details, see the *Identity and Access Management User Guide*.
