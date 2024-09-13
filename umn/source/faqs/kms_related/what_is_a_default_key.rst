:original_name: kms_01_0045.html

.. _kms_01_0045:

What Is a Default Key?
======================

A default key is automatically created by another cloud service using KMS, such as Object Storage Service (OBS). The alias of a default key ends with **/default**.

You can use the management console to query but cannot disable or schedule the deletion of default keys.

Default keys are hosted for free, and are charged based on the number of the API requests for them. If API requests exceed the free limit, the excess part will be charged.

.. table:: **Table 1** Default Master Keys

   =========== ==============================
   Alias       Cloud Service
   =========== ==============================
   obs/default Object Storage Service (OBS)
   evs/default Elastic Volume Service (EVS)
   ims/default Image Management Service (IMS)
   sfs/default Scalable File Service (SFS)
   =========== ==============================

.. note::

   A default key is automatically created when a user employs the KMS encryption function for the first time in another cloud service.
