:original_name: dew_01_0018.html

.. _dew_01_0018:

Permissions Management
======================

If you want to assign different access permissions to employees in an enterprise for the DEW resources purchased on the cloud platform, you can use Identity and Access Management (IAM) to perform refined permission management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users for your employees, and grant permissions to control their access to specific resource types. For example, some software developers in your enterprise need to use DEW resources but must not delete them or perform any high-risk operations. To achieve this result, you can create IAM users for the software developers and grant them only the permissions required for using DEW resources.

If the system account has met your requirements and you do not need to create an independent IAM user for permission control, then you can skip this section. This will not affect other functions of DEW.

Permissions
-----------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from their groups and can perform specified operations on cloud services based on the permissions.

DEW is a project-level service deployed and accessed in specific physical regions. To assign permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. Users need to switch to the authorized region when accessing KMS.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you must also assign other roles that the permissions depend on to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant KMS users only the permissions for managing a certain type of cloud servers. Most policies contain permissions for specific APIs, and permissions are defined using API actions.

For details, see :ref:`Table 1 <dew_01_0018__table123532558115>`.

.. _dew_01_0018__table123532558115:

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

.. table:: **Table 2** CSMS system policies

   +---------------------+------------------------------------------------------------------------------------------------------------------------+--------+------------+
   | Role/Policy         | Description                                                                                                            | Type   | Dependency |
   +=====================+========================================================================================================================+========+============+
   | CSMS FullAccess     | All permissions of CSMS in DEW. Users with these permissions can perform all the operations allowed by policies.       | Policy | None       |
   +---------------------+------------------------------------------------------------------------------------------------------------------------+--------+------------+
   | CSMS ReadOnlyAccess | Read-only permissions of CSMS in DEW. Users with these permissions can perform all the operations allowed by policies. | Policy | None       |
   +---------------------+------------------------------------------------------------------------------------------------------------------------+--------+------------+

:ref:`Table 3 <dew_01_0018__table635410553117>` lists the common operations supported by each system-defined permission of DEW. Select the permissions as needed.

.. _dew_01_0018__table635410553117:

.. table:: **Table 3** Common operations supported by each system-defined policy or role

   +---------------------------------------+-------------------+-------------------+
   | Operation                             | KMS Administrator | KMS CMKFullAccess |
   +=======================================+===================+===================+
   | Create a key                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Enable a key                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Disable a key                         | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Schedule key deletion                 | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Cancel scheduled key deletion         | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Modify a key alias                    | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Modify key description                | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Generate a random number              | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Create a DEK                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Create a plaintext-free DEK           | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Encrypt a DEK                         | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Decrypt a DEK                         | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Obtain parameters for importing a key | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Import key materials                  | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Delete key materials                  | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Create a grant                        | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Revoke a grant                        | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Retire a grant                        | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query the grant list                  | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query retirable grants                | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Encrypt data                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Decrypt data                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Enable key rotation                   | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Modify key rotation interval          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Disable key rotation                  | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query key rotation status             | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query CMK instances                   | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query key tags                        | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query project tags                    | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Batch add or delete key tags          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Add tags to a key                     | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Delete key tags                       | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query the key list                    | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query key details                     | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query instance quantity               | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+
   | Query quotas                          | Y                 | Y                 |
   +---------------------------------------+-------------------+-------------------+

Related Links
-------------

-  Two types of permission policies are provided by default: default policies and custom policies. Default policies are pre-defined by IAM and cannot be modified. If default policies do not meet your requirements, you can create custom policies for fine-grained permission control.
-  Configure permission policies for a user group and add users to the group so that these users can obtain operation permissions defined in the policies.
