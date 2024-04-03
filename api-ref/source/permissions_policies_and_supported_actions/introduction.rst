:original_name: kms_02_0308.html

.. _kms_02_0308:

Introduction
============

This chapter describes fine-grained permissions management for your KMS. If your account does not need individual IAM users, you may skip over this chapter.

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

You can grant permissions to users by using roles and policies. Roles are a type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all of the permissions required to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully.

Supported Actions
-----------------

You can use system-defined policies provided in IAM, or create custom policies to supplement the system-defined policies, implementing refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permission: A statement in a policy that allows or denies certain operations.
-  APIs: REST APIs that can be called in a custom policy.
-  Actions: Added to a custom policy to control permissions for specific operations.
-  Dependent actions: When assigning an action to users, you also need to assign dependent permissions for that action to take effect.
-  IAM projects or enterprise project: Scope of users a permission is granted to. Policies that contain actions supporting both IAM and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect in IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Project.

   .. note::

      Y: supported; x: not supported

KMS supports the following actions that can be defined in custom policies:

:ref:`Manage keys <kms_02_0309>`, such as creating keys and querying keys.
