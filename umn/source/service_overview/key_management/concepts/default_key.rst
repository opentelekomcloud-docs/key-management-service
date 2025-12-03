:original_name: kms_01_0006.html

.. _kms_01_0006:

Default Key
===========

A default key is automatically created by another cloud service using KMS, such as Object Storage Service (OBS). The name of a default key ends with **/default**.

You can use the management console to query the status of Default Master Keys, but cannot disable or schedule the deletion of default keys.

.. table:: **Table 1** Default keys

   =========== =================================
   Key Name    Cloud Service
   =========== =================================
   obs/default Object Storage Service (OBS)
   evs/default Elastic Volume Service (EVS)
   ims/default Image Management Service (IMS)
   sfs/default Scalable File Service (SFS)
   rds/default Relational Database Service (RDS)
   kps/default Key Pair Service (KPS)
   =========== =================================

.. note::

   A Default Master Key is automatically created when a user employs the KMS encryption function for the first time in another cloud service.
