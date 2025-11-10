:original_name: kms_01_0096.html

.. _kms_01_0096:

Querying a Key
==============

Scenario
--------

This section describes how to use the management console to view the information about a custom key, such as its name, status, ID, and creation time. The status of a key can be **Enabled**, **Disabled**, **Pending deletion**, or **Pending import**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. View key details in the key list.


   .. figure:: /_static/images/en-us_image_0000002172783520.png
      :alt: **Figure 1** Key list

      **Figure 1** Key list

   .. note::

      -  Enter the key name in the search box above the key list. Press **Enter**.
      -  You can click |image2| at the upper right corner on top of the key list to show or hide columns of the list.

   :ref:`Table 1 <kms_01_0096__table15653286125723>` describes the parameters of a key list.

   .. _kms_01_0096__table15653286125723:

   .. table:: **Table 1** Key list parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                    |
      +===================================+================================================================================================================================================+
      | Name/ID                           | Name of a key and the random ID of a key generated during its creation                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Status of a key, which can be one of the following:                                                                                            |
      |                                   |                                                                                                                                                |
      |                                   | -  **Enabled**                                                                                                                                 |
      |                                   |                                                                                                                                                |
      |                                   |    The key is enabled.                                                                                                                         |
      |                                   |                                                                                                                                                |
      |                                   | -  **Disabled**                                                                                                                                |
      |                                   |                                                                                                                                                |
      |                                   |    The key is disabled.                                                                                                                        |
      |                                   |                                                                                                                                                |
      |                                   | -  **Pending deletion**                                                                                                                        |
      |                                   |                                                                                                                                                |
      |                                   |    The key is scheduled for deletion.                                                                                                          |
      |                                   |                                                                                                                                                |
      |                                   | -  **Pending import**                                                                                                                          |
      |                                   |                                                                                                                                                |
      |                                   |    If a key does not have any key material, its status is **Pending import**.                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Creation Time                     | Creation time of the key                                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Algorithm and Usage           | Key algorithm selected during key creation and its usage                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Expiration Time                   | Expiration time of the key material. When the material expires, the custom key becomes an empty key.                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Origin                            | Source of key material, which can be one of the following:                                                                                     |
      |                                   |                                                                                                                                                |
      |                                   | -  **External**                                                                                                                                |
      |                                   |                                                                                                                                                |
      |                                   |    The key uses an imported key material.                                                                                                      |
      |                                   |                                                                                                                                                |
      |                                   | -  Key Management Service                                                                                                                      |
      |                                   |                                                                                                                                                |
      |                                   |    The key uses KMS-generated material.                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Operations you can perform on the CMK, such as disable, delete, import key material, or cancel deletion. You can also assign keys to projects. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click the key name to view its details.


   .. figure:: /_static/images/en-us_image_0000002208041185.png
      :alt: **Figure 2** Viewing key details

      **Figure 2** Viewing key details

   .. note::

      To change the alias or description of the CMK, click |image3| next to **Name** or **Description**.

      -  The name and description of the default key cannot be modified. The name of the default key ends with **/default**.
      -  The name and description of a key cannot be changed if the key is in **Pending deletion** status.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0000002208027189.png
.. |image3| image:: /_static/images/en-us_image_0000002171452720.png
