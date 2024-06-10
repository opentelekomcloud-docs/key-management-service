:original_name: kms_01_0049.html

.. _kms_01_0049:

Why Cannot I Delete a CMK Immediately?
======================================

The decision to delete a CMK should be considered with great caution. Before deletion, confirm that the CMK's encrypted data has all been migrated. As soon as the CMK is deleted, you will not be able to decrypt data with it. Therefore, KMS offers a user-specified period of 7 to 1096 days for the deletion to finally take effect. On the scheduled day of deletion, the CMK will be permanently deleted. However, prior to the scheduled day, you can still cancel the pending deletion. This is a means of precaution within KMS.
