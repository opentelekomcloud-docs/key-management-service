:original_name: kms_01_9996.html

.. _kms_01_9996:

Creating a Custom KMS Policy
============================

Custom policies can be created as a supplement to the system policies of KMS. For details about the actions supported by custom policies, see "Permissions Policies and Supported Actions" in *Key Management Service API Reference*.

You can create custom policies in either of the following ways:

-  Visual editor: You can select policy configurations without the need to know policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

Example Custom Policies
-----------------------

-  Example: authorizing users to create and import keys

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "kms:cmk:create",
                      "kms:cmk:getMaterial",
                      "kms:cmkTag:create",
                      "kms:cmkTag:batch",
                      "kms:cmk:importMaterial"
                  ]
              }
          ]
      }

-  Example: authorizing users to use keys

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "kms:dek:crypto",
                      "kms:cmk:get",
                      "kms:cmk:crypto",
                      "kms:cmk:generate",
                      "kms:cmk:list"
                  ]
              }
          ]
      }

-  Example: multi-action policy

   A custom policy can contain actions of multiple services that are all of the global or project-level type. The following is a policy with multiple statements:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "rds:task:list"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "kms:dek:crypto",
                      "kms:cmk:get",
                      "kms:cmk:crypto",
                      "kms:cmk:generate",
                      "kms:cmk:list"
                  ]
              }
          ]
      }
