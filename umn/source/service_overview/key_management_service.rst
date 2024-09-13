:original_name: kms_01_0299.html

.. _kms_01_0299:

Key Management Service
======================

Key Management Service (KMS) is a secure, reliable, and easy-to-use service that helps users centrally manage and safeguard their Customer Master Keys (CMKs).

KMS uses hardware security modules (HSMs) to protect CMKs. HSMs help you create and control CMKs with ease. All CMKs are protected by root keys in HSMs to avoid leakage.

It also controls access to keys and records all operations on keys with traceable logs. In addition, it provides use records of all keys, meeting your audit and regulatory compliance requirements.

.. table:: **Table 1** Basic concepts

   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                | Definition                                                                                                                                                                                                                                                                                                       |
   +=====================================+==================================================================================================================================================================================================================================================================================================================+
   | Customer Master Key                 | A CMK is a main encryption key created by a user using KMS. It is used to encrypt and protect data encryption keys (DEKs). One CMK can be used to encrypt one or more DEKs.                                                                                                                                      |
   |                                     |                                                                                                                                                                                                                                                                                                                  |
   | (CMK)                               |                                                                                                                                                                                                                                                                                                                  |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Default Key                         | A default key is automatically created by another cloud service using KMS, such as Object Storage Service (OBS). The alias of a default key ends with **/default**. For details about the corresponding cloud services, see :ref:`Default Master Keys <kms_01_0299__en-us_topic_0112946998_table2077517211519>`. |
   |                                     |                                                                                                                                                                                                                                                                                                                  |
   |                                     | You can use the management console to query the status of Default Master Keys, but cannot disable or schedule the deletion of default keys.                                                                                                                                                                      |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Encryption Key                 | A data encryption key (DEK) is a key used for encrypting data.                                                                                                                                                                                                                                                   |
   |                                     |                                                                                                                                                                                                                                                                                                                  |
   | (DEK)                               |                                                                                                                                                                                                                                                                                                                  |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Hardware Security Module (HSM)      | A hardware device that securely produces, stores, manages, and uses keys and provides encryption services.                                                                                                                                                                                                       |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | True Random Number Generator (TRNG) | A device that generates random numbers through physical processes instead of computer programs.                                                                                                                                                                                                                  |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Project                             | A project is used to group and isolate OpenStack resources, including computing, storage, and network resources. A project can be a department or a project team.                                                                                                                                                |
   |                                     |                                                                                                                                                                                                                                                                                                                  |
   |                                     | Multiple projects can be created for one account.                                                                                                                                                                                                                                                                |
   +-------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _kms_01_0299__en-us_topic_0112946998_table2077517211519:

.. table:: **Table 2** Default keys

   =========== ==============================
   Alias       Cloud Service
   =========== ==============================
   obs/default Object Storage Service (OBS)
   evs/default Elastic Volume Service (EVS)
   ims/default Image Management Service (IMS)
   =========== ==============================

.. note::

   A default key is automatically created when a user employs the KMS encryption function for the first time in another cloud service.
