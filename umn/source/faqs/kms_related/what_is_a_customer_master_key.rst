:original_name: kms_01_0044.html

.. _kms_01_0044:

What Is a Customer Master Key?
==============================

A Customer Master Key (CMK) is a Key Encryption Key (KEK) created by a user on KMS. It is used to encrypt and protect DEKs. One CMK can be used to encrypt one or more DEKs.

CMKs are categorized into custom keys and default keys.

-  Custom keys

   Keys created or imported by users on the KMS console.

-  Default keys

   When a user uses KMS for encryption in a cloud service for the first time, the cloud service automatically creates a key with the alias suffix **/default**.

   You can use the management console to query but cannot disable or schedule the deletion of Default Master Keys.

   .. table:: **Table 1** Default Master Keys

      =========== ==============================
      Alias       Cloud Service
      =========== ==============================
      obs/default Object Storage Service (OBS)
      evs/default Elastic Volume Service (EVS)
      ims/default Image Management Service (IMS)
      sfs/default Scalable File Service (SFS)
      =========== ==============================
