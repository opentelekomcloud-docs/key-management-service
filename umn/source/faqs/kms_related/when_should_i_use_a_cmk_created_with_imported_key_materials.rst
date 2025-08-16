:original_name: kms_01_0102.html

.. _kms_01_0102:

When Should I Use a CMK Created with Imported Key Materials?
============================================================

-  If you do not want to use KMS-generated key materials, you can import your own key materials to create a CMK. Such a CMK allows deletion of only the key materials when you do not need it. In addition, when you find that the key materials are mis-deleted, you can import the same materials to the CMK.
-  You can also import off-cloud key materials to KMS when you want to use the same keys on and off the cloud. This practice has proved useful when users migrate local encrypted data onto cloud.
