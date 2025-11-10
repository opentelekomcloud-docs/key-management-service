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

#. Click the name of the target custom key to view its details.

#. Information about the custom key and grants created on it are displayed, as shown in .

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
      | Granted Operations | Authorized operations (such as **Create Data Key**) on the custom key             |
      +--------------------+-----------------------------------------------------------------------------------+
      | Creation Time      | Creation time of the grant                                                        |
      +--------------------+-----------------------------------------------------------------------------------+
      | Operation          | Operations that can be performed on a grant. For example, you can revoke a grant. |
      +--------------------+-----------------------------------------------------------------------------------+

#. Click a grant ID to view the grant details. shows an example.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
