:original_name: kms_01_0016.html

.. _kms_01_0016:

Related Services
================

OBS
---

Object Storage Service (OBS) is a scalable service that provides secure, reliable, and cost-effective cloud storage for massive amounts of data. KMS provides central management and control capabilities of CMKs for OBS. It is used for server-side encryption with KMS-managed keys (SSE-KMS) on OBS.

EVS
---

Elastic Volume Service (EVS) offers scalable block storage for cloud servers. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouse applications, and high-performance computing (HPC) scenarios to meet diverse service requirements. KMS provides central management and control capabilities of CMKs for EVS. It is used for encryption in EVS.

IMS
---

Image Management Service (IMS) allows you to manage the entire lifecycle of your images. KMS provides central management and control capabilities of CMKs for Image Management Service (IMS). It is used for private image encryption in IMS.

SFS
---

Scalable File Service (SFS) provides high-performance file storage (NAS) that can be expanded on demand. KMS provides central management and control capabilities of CMKs for SFS. It is used for file system encryption in SFS.

RDS
---

Relational Database Service (RDS) is a cloud relational database that is reliable, scalable, easy to manage, and immediately ready for use. KMS provides central management and control capabilities of CMKs for RDS. It is used for disk encryption in RDS.

DDS
---

Document Database Service (DDS) is a MongoDB-compatible database service that is secure, highly available, reliable, scalable, and easy to use. It provides DB instance creation, scaling, redundancy, backup, restoration, monitoring, and alarm reporting functions with just a few clicks on the DDS console. KMS provides central management and control capabilities of CMKs for DDS. It is used for disk encryption in DDS.

CTS
---

Cloud Trace Service (CTS) provides you with a history of KMS operations. After the CTS service is enabled, you can view all generated traces to review and audit performed KMS operations. For details, see the *Cloud Trace Service User Guide*.

.. table:: **Table 1** KMS operations supported by CTS

   +---------------------------------+---------------+-------------------------------+
   | Operation                       | Resource Type | Trace Name                    |
   +=================================+===============+===============================+
   | Create a key                    | CMK           | createKey                     |
   +---------------------------------+---------------+-------------------------------+
   | Create a DEK                    | CMK           | createDataKey                 |
   +---------------------------------+---------------+-------------------------------+
   | Create a plaintext-free DEK     | CMK           | createDataKeyWithoutPlaintext |
   +---------------------------------+---------------+-------------------------------+
   | Enable a key                    | CMK           | enableKey                     |
   +---------------------------------+---------------+-------------------------------+
   | Disable a key                   | CMK           | disableKey                    |
   +---------------------------------+---------------+-------------------------------+
   | Encrypt a DEK                   | CMK           | encryptDatakey                |
   +---------------------------------+---------------+-------------------------------+
   | Decrypt a DEK                   | CMK           | decryptDatakey                |
   +---------------------------------+---------------+-------------------------------+
   | Schedule key deletion           | CMK           | scheduleKeyDeletion           |
   +---------------------------------+---------------+-------------------------------+
   | Cancel scheduled key deletion   | CMK           | cancelKeyDeletion             |
   +---------------------------------+---------------+-------------------------------+
   | Generate random numbers         | RNG           | genRandom                     |
   +---------------------------------+---------------+-------------------------------+
   | Modify a key alias              | CMK           | updateKeyAlias                |
   +---------------------------------+---------------+-------------------------------+
   | Modify key description          | CMK           | updateKeyDescription          |
   +---------------------------------+---------------+-------------------------------+
   | Prompt risks about CMK deletion | CMK           | deleteKeyRiskTips             |
   +---------------------------------+---------------+-------------------------------+
   | Import key materials            | CMK           | importKeyMaterial             |
   +---------------------------------+---------------+-------------------------------+
   | Delete key materials            | CMK           | deleteImportedKeyMaterial     |
   +---------------------------------+---------------+-------------------------------+
   | Create a grant                  | CMK           | createGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Retire a grant                  | CMK           | retireGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Revoke a grant                  | CMK           | revokeGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Encrypt data                    | CMK           | encryptData                   |
   +---------------------------------+---------------+-------------------------------+
   | Decrypt data                    | CMK           | decryptData                   |
   +---------------------------------+---------------+-------------------------------+
   | Add a tag                       | CMK           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Delete a tag                    | CMK           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Add tags in batches             | CMK           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Delete tags in batches          | CMK           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Enable key rotation             | CMK           | enableKeyRotation             |
   +---------------------------------+---------------+-------------------------------+
   | Modify key rotation interval    | CMK           | updateKeyRotationInterval     |
   +---------------------------------+---------------+-------------------------------+
   | Disable key rotation            | CMK           | disableKeyRotation            |
   +---------------------------------+---------------+-------------------------------+

IAM
---

Identity and Access Management (IAM) provides the permission management function for KMS.

Only users who have KMS Administrator permissions can use KMS.

To apply for permissions, contact a user with Security Administrator permissions. For details, see the *Identity and Access Management User Guide*.
