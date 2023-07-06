:original_name: kms_01_0074.html

.. _kms_01_0074:

What Is a Customer Master Key?
==============================

A Customer Master Key (CMK) is a Key Encryption Key (KEK) created by a user using KMS. It is used to encrypt and protect Data Encryption Keys (DEKs). One CMK can be used to encrypt one or multiple DEKs.

CMKs are categorized into custom keys and default keys.

-  Custom keys

   Keys created or imported by users on the KMS console.

-  Default keys

   When a user uses KMS for encryption in a cloud service for the first time, the cloud service automatically creates a key with the alias suffix **/default**.

   On the KMS console, you can query Default Master Keys, but can neither disable them nor schedule their deletion.

   .. table:: **Table 1** Default Master Keys

      =========== ==============================
      Alias       Cloud Service
      =========== ==============================
      obs/default Object Storage Service (OBS)
      evs/default Elastic Volume Service (EVS)
      ims/default Image Management Service (IMS)
      sfs/default Scalable File Service (SFS)
      =========== ==============================
