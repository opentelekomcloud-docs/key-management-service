:original_name: dew_01_8887.html

.. _dew_01_8887:

Viewing a Secret
================

This section describes how to check secret names, statuses, and creation time on the CSMS console. The secret status can be **Enabled** or **Pending deletion**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Check the secret list. For more information, see :ref:`Table 1 <dew_01_8887__table1011437111712>`.


   .. figure:: /_static/images/en-us_image_0000002278808133.png
      :alt: **Figure 1** Secret list

      **Figure 1** Secret list

   .. _dew_01_8887__table1011437111712:

   .. table:: **Table 1** Secret list parameters

      +--------------------+---------------------------------------------------------------------------+
      | Parameter          | Description                                                               |
      +====================+===========================================================================+
      | Secret Name/ID     | Secret name and ID                                                        |
      +--------------------+---------------------------------------------------------------------------+
      | Status             | Status of a secret. The value can be **Enabled** or **Pending deletion**. |
      +--------------------+---------------------------------------------------------------------------+
      | Type               | Only shared secrets are supported.                                        |
      +--------------------+---------------------------------------------------------------------------+
      | Associated events  | Bound event notification when the secret was created.                     |
      +--------------------+---------------------------------------------------------------------------+
      | Created            | Time when the secret is created                                           |
      +--------------------+---------------------------------------------------------------------------+
      | Enterprise Project | Enterprise project that the secret is to be bound to                      |
      +--------------------+---------------------------------------------------------------------------+

#. Click a secret to view its details, as shown in :ref:`Figure 2 <dew_01_8887__fig14725810113147>`.

   -  You can click **Edit** to modify the encryption key and description of a secret.

   -  You can click **Refresh** to refresh secret information.

      .. _dew_01_8887__fig14725810113147:

      .. figure:: /_static/images/en-us_image_0000002278728677.png
         :alt: **Figure 2** Secret details

         **Figure 2** Secret details

.. |image1| image:: /_static/images/en-us_image_0000002195603692.png
.. |image2| image:: /_static/images/en-us_image_0000002195444124.png
