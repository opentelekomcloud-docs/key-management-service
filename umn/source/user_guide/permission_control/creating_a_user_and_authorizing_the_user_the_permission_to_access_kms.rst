:original_name: kms_01_0135.html

.. _kms_01_0135:

Creating a User and Authorizing the User the Permission to Access KMS
=====================================================================

This section describes IAM's fine-grained permissions management for your KMS resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has its own security credentials to access KMS resources.
-  Grant users only the permissions required to perform a task.
-  Entrust an account or cloud service to perform efficient O&M on your KMS resources.

If your account does not need individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <kms_01_0135__fig23111471897>`).

Prerequisites
-------------

Before granting permissions to a user group, you need to understand the available KMS permissions, and grant permissions based on the real-life scenario. The following tables describe the permissions supported in KMS.

.. table:: **Table 1** KMS permissions

   +-----------------------+--------------------------------------------------+--------+
   | Role/Policy           | Description                                      | Type   |
   +=======================+==================================================+========+
   | KMS Administrator     | Administrator permissions for the encryption key | Role   |
   +-----------------------+--------------------------------------------------+--------+
   | KMS CMKFullAccess     | All permissions for the encryption keys          | Policy |
   +-----------------------+--------------------------------------------------+--------+
   | KMS CMK Admin         | All permissions for the encryption keys          | Policy |
   +-----------------------+--------------------------------------------------+--------+
   | KMS CMKReadOnlyAccess | Read-only permission for encryption keys         | Policy |
   +-----------------------+--------------------------------------------------+--------+

Authorization Process
---------------------

.. _kms_01_0135__fig23111471897:

.. figure:: /_static/images/en-us_image_0220982951.png
   :alt: **Figure 1** Authorizing the KMS access permission to a user

   **Figure 1** Authorizing the KMS access permission to a user

#. .. _kms_01_0135__li960014441019:

   Create a user group on the IAM console and grant the user group the permission (indicating full permissions for keys).

#. Create a user on the IAM console and add the user to the user group created in :ref:`1 <kms_01_0135__li960014441019>`.

#. Log in to the console as newly created user, and verify that the user only has the assigned permissions.
