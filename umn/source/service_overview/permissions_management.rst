:original_name: kms_01_9999.html

.. _kms_01_9999:

Permissions Management
======================

If you want to assign different access permissions to employees in an enterprise for the KMS resources purchased on the cloud platform, you can use Identity and Access Management (IAM) to perform refined permission management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to control their access to specific resource types. For example, if you have software developers and you want to assign them the permission to access KMS but not to delete KMS or its resources, then you can create an IAM policy to assign the developers the permission to access KMS but prevent them from deleting KMS related data.

If the system account has met your requirements and you do not need to create an independent IAM user for permission control, then you can skip this section. This will not affect other functions of KMS.

KMS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups they are added to and can perform specified operations on cloud services based on the permissions.

KMS is a project-level service deployed and accessed in specific physical regions. To assign permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. Users need to switch to the authorized region when accessing KMS.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you must also assign other roles that the permissions depend on to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant KMS users only the permissions for managing a certain type of cloud servers. Most policies contain permissions for specific APIs, and permissions are defined using API actions.

For more information, see :ref:`Table 1 <kms_01_9999__en-us_topic_0169425412_table123532558115>`.

.. _kms_01_9999__en-us_topic_0169425412_table123532558115:

.. table:: **Table 1** KMS permissions

   +-------------------+--------------------------------------------------+---------------+
   | Role/Policy Name  | Description                                      | Type          |
   +===================+==================================================+===============+
   | KMS Administrator | Administrator permissions for the encryption key | System role   |
   +-------------------+--------------------------------------------------+---------------+
   | KMS CMKFullAccess | All permissions for the encryption keys          | System policy |
   +-------------------+--------------------------------------------------+---------------+

The following table describes the common operations supported by each system-defined permission of KMS. Select the permissions as needed.

.. table:: **Table 2** Common operations supported by each system-defined policy or role

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
   | Revoking a grant                      | Y                 | Y                 |
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
