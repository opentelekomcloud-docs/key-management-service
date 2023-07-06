:original_name: kms_01_0030.html

.. _kms_01_0030:

Querying a Grant
================

Scenario
--------

This section describes how to view the details about a grant, such as the grant ID, grantee user ID, granted operation, and creation time.

Prerequisites
-------------

You have created a grant.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the alias of the desired CMK to view its details.

#. Information about the CMK and grants created on it are displayed, :ref:`Figure 1 <kms_01_0030__fig26845936115420>` shows example grant information.

   .. _kms_01_0030__fig26845936115420:

   .. figure:: /_static/images/en-us_image_0129264298.png
      :alt: **Figure 1** Querying a grant

      **Figure 1** Querying a grant

   :ref:`Table 1 <kms_01_0030__table41279785172331>` provides more details.

   .. _kms_01_0030__table41279785172331:

   .. table:: **Table 1** Parameter description

      +--------------------+-----------------------------------------------------------------------------------+
      | Parameter          | Description                                                                       |
      +====================+===================================================================================+
      | Grant ID           | Randomly generated unique identification of a grant                               |
      +--------------------+-----------------------------------------------------------------------------------+
      | Grantee            | ID of an authorized user.                                                         |
      +--------------------+-----------------------------------------------------------------------------------+
      | Granted Operations | Authorized operations (such as **Create Data Key**) on the CMK                    |
      +--------------------+-----------------------------------------------------------------------------------+
      | Creation Time      | Creation time of the grant                                                        |
      +--------------------+-----------------------------------------------------------------------------------+
      | Operation          | Operations that can be performed on a grant. For example, you can revoke a grant. |
      +--------------------+-----------------------------------------------------------------------------------+

#. Click a grant ID to view the grant details, :ref:`Figure 2 <kms_01_0030__fig962432095216>` shows example grant information.

   .. _kms_01_0030__fig962432095216:

   .. figure:: /_static/images/en-us_image_0129264350.png
      :alt: **Figure 2** Viewing grant details

      **Figure 2** Viewing grant details

.. |image1| image:: /_static/images/en-us_image_0237800345.png
