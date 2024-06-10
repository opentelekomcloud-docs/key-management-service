:original_name: kms_01_0017.html

.. _kms_01_0017:

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

Relational Database Service (RDS) is a relational database that is reliable, scalable, easy to manage, and immediately ready for use. KMS provides central management and control capabilities of CMKs for RDS. It is used for disk encryption in relational databases.

CTS
---

Cloud Trace Service (CTS) provides you with a history of KMS operations. After the CTS service is enabled, you can view all generated traces to review and audit performed KMS operations. For details, see the *Cloud Trace Service User Guide*.

.. table:: **Table 1** KMS operations supported by CTS

   +---------------------------------+---------------+-------------------------------+
   | Operation                       | Resource Type | Trace Name                    |
   +=================================+===============+===============================+
   | Create a key                    | cmk           | createKey                     |
   +---------------------------------+---------------+-------------------------------+
   | Create a DEK                    | cmk           | createDataKey                 |
   +---------------------------------+---------------+-------------------------------+
   | Create a plaintext-free DEK     | cmk           | createDataKeyWithoutPlaintext |
   +---------------------------------+---------------+-------------------------------+
   | Enable a key                    | cmk           | enableKey                     |
   +---------------------------------+---------------+-------------------------------+
   | Disable a key                   | cmk           | disableKey                    |
   +---------------------------------+---------------+-------------------------------+
   | Encrypt a DEK                   | cmk           | encryptDatakey                |
   +---------------------------------+---------------+-------------------------------+
   | Decrypt a DEK                   | cmk           | decryptDatakey                |
   +---------------------------------+---------------+-------------------------------+
   | Schedule key deletion           | cmk           | scheduleKeyDeletion           |
   +---------------------------------+---------------+-------------------------------+
   | Cancel scheduled key deletion   | cmk           | cancelKeyDeletion             |
   +---------------------------------+---------------+-------------------------------+
   | Generate random numbers         | rng           | genRandom                     |
   +---------------------------------+---------------+-------------------------------+
   | Modify a key alias              | cmk           | updateKeyAlias                |
   +---------------------------------+---------------+-------------------------------+
   | Modify key description          | cmk           | updateKeyDescription          |
   +---------------------------------+---------------+-------------------------------+
   | Prompt risks about CMK deletion | cmk           | deleteKeyRiskTips             |
   +---------------------------------+---------------+-------------------------------+
   | Import key materials            | cmk           | importKeyMaterial             |
   +---------------------------------+---------------+-------------------------------+
   | Delete key materials            | cmk           | deleteImportedKeyMaterial     |
   +---------------------------------+---------------+-------------------------------+
   | Create a grant                  | cmk           | createGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Retire a grant                  | cmk           | retireGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Revoke a grant                  | cmk           | revokeGrant                   |
   +---------------------------------+---------------+-------------------------------+
   | Encrypt data                    | cmk           | encryptData                   |
   +---------------------------------+---------------+-------------------------------+
   | Decrypt data                    | cmk           | decryptData                   |
   +---------------------------------+---------------+-------------------------------+
   | Add a tag                       | cmk           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Delete a tag                    | cmk           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Add tags in batches             | cmk           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Delete tags in batches          | cmk           | dealUnifiedTags               |
   +---------------------------------+---------------+-------------------------------+
   | Enable key rotation             | cmk           | enableKeyRotation             |
   +---------------------------------+---------------+-------------------------------+
   | Modify key rotation interval    | cmk           | updateKeyRotationInterval     |
   +---------------------------------+---------------+-------------------------------+
   | Disable key rotation            | cmk           | disableKeyRotation            |
   +---------------------------------+---------------+-------------------------------+

IAM
---

Identity and Access Management (IAM) provides the permission management function for KMS.

Only users who have KMS Administrator permissions can use KMS.

To apply for permissions, contact a user with Security Administrator permissions. For details, see the *Identity and Access Management User Guide*.
