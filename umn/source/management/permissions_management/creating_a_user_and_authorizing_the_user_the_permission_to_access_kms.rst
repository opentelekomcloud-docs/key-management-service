:original_name: kms_01_9997.html

.. _kms_01_9997:

Creating a User and Authorizing the User the Permission to Access KMS
=====================================================================

This section describes IAM's fine-grained permissions management for your KMS resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has its own security credentials to access KMS resources.
-  Grant users only the permissions required to perform a task.
-  Entrust an account or cloud service to perform efficient O&M on your KMS resources.

If your account does not need individual IAM users, you may skip over this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <kms_01_9997__en-us_topic_0169425415_fig23111471897>`).

Prerequisites
-------------

Before authorizing permissions to a user group, you need to know which KMS permissions can be added to the user group. :ref:`Table 1 <kms_01_9997__en-us_topic_0169425415_table159711515155618>` lists the KMS system policies.

.. _kms_01_9997__en-us_topic_0169425415_table159711515155618:

.. table:: **Table 1** KMS permissions

   +-------------------+--------------------------------------------------+---------------+------------+
   | Role/Policy Name  | Description                                      | Type          | Dependency |
   +===================+==================================================+===============+============+
   | KMS Administrator | Administrator permissions for the encryption key | System role   | None       |
   +-------------------+--------------------------------------------------+---------------+------------+
   | KMS CMKFullAccess | All permissions for the encryption key           | System policy | None       |
   +-------------------+--------------------------------------------------+---------------+------------+

Authorization Process
---------------------

.. _kms_01_9997__en-us_topic_0169425415_fig23111471897:

.. figure:: /_static/images/en-us_image_0220982951.png
   :alt: **Figure 1** Authorizing the KMS access permission to a user

   **Figure 1** Authorizing the KMS access permission to a user

#. .. _kms_01_9997__en-us_topic_0169425415_li960014441019:

   Create a user group on the IAM console and grant the user group the **KMS CMKFullAccess** permission (indicating full permissions for keys).

#. Create a user on the IAM console and add the user to the user group created in :ref:`1 <kms_01_9997__en-us_topic_0169425415_li960014441019>`.
