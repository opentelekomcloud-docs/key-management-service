:original_name: dew_01_0135.html

.. _dew_01_0135:

Creating a User and Authorizing the User the Permission to Access DEW
=====================================================================

This section describes IAM's fine-grained permissions management for your DEW resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has its own security credentials to access DEW resources.
-  Grant users only the permissions required to perform a task.
-  Entrust an account or cloud service to perform efficient O&M on your KMS resources.

If your account does not need individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <dew_01_0135__fig23111471897>`).

Prerequisites
-------------

Before granting permissions to a user group, you need to understand the available DEW permissions, and grant permissions based on the real-life scenario. The following tables describe the permissions supported in DEW.

.. table:: **Table 1** DEW permissions

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

.. _dew_01_0135__fig23111471897:

.. figure:: /_static/images/en-us_image_0220982951.png
   :alt: **Figure 1** Authorizing the DEW access permission to a user

   **Figure 1** Authorizing the DEW access permission to a user

#. .. _dew_01_0135__li960014441019:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Create a user group on the IAM console and grant the user group the **KMS CMKFullAccess** permission (indicating full permissions for keys).

#. `Create a user and add it to a user group. <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__

   Create a user on the IAM console and add the user to the user group created in :ref:`1 <dew_01_0135__li960014441019>`.

#. `Log in as the created user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the console as newly created user, and verify that the user only has the assigned permissions.

Tenant Guest Roles
------------------

If you have configured Tenant Guest permissions for the IAM account, apart from the read-only permissions for all cloud services except Identity and Access Management (IAM), you also have the following KMS permissions:

-  **kms:cmk:create**: Create a key.
-  **kms:cmk:createDataKey**: Create a DEK.
-  **kms:cmk:createDataKeyWithoutPlaintext**: Create a plaintext-free DEK.
-  **kms:cmk:encryptDataKey**: Encrypt the DEK.
-  **kms:cmk:decryptDataKey**: Decrypt a DEK.
-  **kms:cmk:retireGrant**: Retire a grant.
-  **kms:cmk:decryptData**: Decrypt data.
-  **kms:cmk:encryptData**: Encrypt data.
-  **kms::generateRandom**: Generate a random number.

If you want to configure the Tenant Guest role for an IAM user but do not want to have the preceding permissions, you need to configure a custom deny policy for the IAM user. For details about how to configure a custom policy, see :ref:`Creating a Custom KMS Policy <dew_01_0161>`.
