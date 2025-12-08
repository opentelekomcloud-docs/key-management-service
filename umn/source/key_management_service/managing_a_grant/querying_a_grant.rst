:original_name: dew_01_0097.html

.. _dew_01_0097:

Querying a Grant
================

You can view the details about a custom key grant on the KMS console, such as the grant ID, grantee user ID, granted operation, and creation time.

Prerequisites
-------------

You have created a grant.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Key Management Service**.

#. Click the alias of the target custom key to view its details.

#. Click **Grant** to view the created grant of the current custom key. :ref:`Table 1 <dew_01_0097__t0484dc5b4d9e4d86a61df05bffcaecf3>` describes the parameters.

   .. _dew_01_0097__t0484dc5b4d9e4d86a61df05bffcaecf3:

   .. table:: **Table 1** Parameters

      +--------------------+-----------------------------------------------------------------------+
      | Parameter          | Description                                                           |
      +====================+=======================================================================+
      | Grant Name         | Name of the grant when created                                        |
      +--------------------+-----------------------------------------------------------------------+
      | Grantee ID         | ID of the authorized user or account.                                 |
      +--------------------+-----------------------------------------------------------------------+
      | Granted To         | Whether permissions are granted to a user or account.                 |
      +--------------------+-----------------------------------------------------------------------+
      | Granted Operations | Authorized operations (such as **Create Data Key**) on the custom key |
      +--------------------+-----------------------------------------------------------------------+
      | Created            | Time when the grant is created                                        |
      +--------------------+-----------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511520841.png
