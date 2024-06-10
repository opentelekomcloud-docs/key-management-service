:original_name: kms_01_0179.html

.. _kms_01_0179:

Viewing a CMK
=============

This section describes how to view the information about the custom key on the KMS console, including the key alias, status, ID, and creation time. The status of a key can be **Enabled**, **Disabled**, **Scheduled deletion**, or **Pending import**.

Procedure
---------

#. Log in to the management console.
#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

3. Check the key list.

   .. table:: **Table 1** Key list parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                    |
      +===================================+================================================================================================================================================+
      | Alias/ID                          | Alias of a key and the random ID of a key generated during its creation.                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Status of a CMK, which can be one of the following:                                                                                            |
      |                                   |                                                                                                                                                |
      |                                   | -  **Enabled**                                                                                                                                 |
      |                                   |                                                                                                                                                |
      |                                   |    The CMK is enabled.                                                                                                                         |
      |                                   |                                                                                                                                                |
      |                                   | -  **Disabled**                                                                                                                                |
      |                                   |                                                                                                                                                |
      |                                   |    The CMK is disabled.                                                                                                                        |
      |                                   |                                                                                                                                                |
      |                                   | -  **Pending deletion**                                                                                                                        |
      |                                   |                                                                                                                                                |
      |                                   |    The CMK is scheduled for deletion.                                                                                                          |
      |                                   |                                                                                                                                                |
      |                                   | -  **Pending import**                                                                                                                          |
      |                                   |                                                                                                                                                |
      |                                   |    If your CMK does not have materials, its status is **Pending import**.                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Algorithm and Usage           | Key algorithm selected during key creation and its usage                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Origin                            | Source of key material, which can be one of the following:                                                                                     |
      |                                   |                                                                                                                                                |
      |                                   | -  **External**                                                                                                                                |
      |                                   |                                                                                                                                                |
      |                                   |    The key is imported to the KMS from an external system.                                                                                     |
      |                                   |                                                                                                                                                |
      |                                   | -  **Key Management Service**                                                                                                                  |
      |                                   |                                                                                                                                                |
      |                                   |    The key is a default key or created in KMS.                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Operations you can perform on the key, such as disable, delete, import key material, or cancel deletion. You can also assign keys to projects. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

4. You can click the alias of a key to view its details.

   .. note::

      To change the alias or description of the CMK, click |image2| next to the value of **Alias** or **Description**.

      -  A default key (the alias suffix of which is **/default**) does not allow alias and description changes.
      -  The alias and description of a CMK cannot be changed if the CMK is in **Pending deletion** status.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
.. |image2| image:: /_static/images/en-us_image_0231665754.png
