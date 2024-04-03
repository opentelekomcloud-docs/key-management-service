:original_name: kms_02_0054.html

.. _kms_02_0054:

Concepts
========

-  Account

   An account has full access permissions for all the resources and cloud services under it. It can reset user passwords and grant users permissions. The account is a payment entity and should not be used to perform routine management. For security purposes, create IAM users and grant them permissions for routine management.

-  User

   An IAM user is created by an account to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   The account name, username, and password wll be required for API authentication.

-  Region

   Regions are divided based on geographical location and network latency. Public services, such as Elastic Cloud Server (ECS), Elastic Volume Service (EVS), Object Storage Service (OBS), Virtual Private Cloud (VPC), Elastic IP (EIP), and Image Management Service (IMS), are shared within the same region. Regions are classified as universal regions and dedicated regions. A universal region provides universal cloud services for common tenants. A dedicated region provides services of the same type only or for specific tenants.

-  Availability Zone (AZ)

   An AZ comprises one or multiple physical data centers equipped with independent ventilation, fire, water, and electricity facilities. Compute, network, storage, and other resources in an AZ are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to support cross-AZ high-availability systems.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. For more refined access control, create subprojects under a project and create resources in the subprojects. Users can then be assigned permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0264400728.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model
