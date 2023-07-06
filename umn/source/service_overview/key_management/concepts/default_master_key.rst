:original_name: kms_01_0006.html

.. _kms_01_0006:

Default Master Key
==================

A Default Master Key is automatically created by another cloud service using KMS, such as Object Storage Service (OBS). The alias of a Default Master Key ends with **/default**.

You can use the management console to query the status of Default Master Keys, but cannot disable or schedule the deletion of Default Master Keys.

.. table:: **Table 1** Default Master Keys

   =========== =================================
   Alias       Cloud Service
   =========== =================================
   obs/default OBS
   evs/default Elastic Volume Service (EVS)
   ims/default Image Management Service (IMS)
   sfs/default Scalable File Service (SFS)
   rds/default Relational Database Service (RDS)
   =========== =================================

.. note::

   A Default Master Key is automatically created when a user employs the KMS encryption function for the first time in another cloud service.
