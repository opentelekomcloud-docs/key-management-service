:original_name: kms_01_0182.html

.. _kms_01_0182:

What Should I Do If I Do Not Have the Permissions to Perform Operations on KMS?
===============================================================================

Symptom
-------

A message indicating lack of permissions is displayed when you attempt to perform operations on keys, such as view, create, or import keys.

Possible Causes
---------------

Your account is not associated with the required KMS system policies.

Solution
--------

#. Check whether your account has been associated with **KMS Administrator** and **KMS CMKFullAccess** policies.

   For details about how to check your user groups and permissions, see the "User Groups and Authorization" section.

   If your account has been associated with required KMS system policies, go to :ref:`2 <kms_01_0182__li0304204663910>`.

#. .. _kms_01_0182__li0304204663910:

   Associate your account with required system policies.

   -  For details about how to add administrator permissions, see the "User Groups and Authorization" section.
   -  For details about how to add a custom policy, see the "Creating a Custom KMS Policy" section.
