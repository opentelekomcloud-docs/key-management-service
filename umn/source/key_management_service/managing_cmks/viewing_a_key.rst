:original_name: dew_01_0179.html

.. _dew_01_0179:

Viewing a Key
=============

This section describes how to view the information about the custom key on the KMS console, including thekey name/ID and the creation time. The status of a key can be **Enabled**, **Disabled**, **Scheduled deletion**, or **Pending import**.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| on the left and choose **Security** > **Key Management Service**.

4. Check the key list.

   .. table:: **Table 1** Key list parameters

      +-----------------------------------+---------------------------------------------------------------------------+
      | Parameter                         | Description                                                               |
      +===================================+===========================================================================+
      | Name/ID                           | Name of a key and the random ID of a key generated during its creation.   |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Status                            | Status of a CMK, which can be one of the following:                       |
      |                                   |                                                                           |
      |                                   | -  **Enabled**                                                            |
      |                                   |                                                                           |
      |                                   |    The CMK is enabled.                                                    |
      |                                   |                                                                           |
      |                                   | -  **Disabled**                                                           |
      |                                   |                                                                           |
      |                                   |    The CMK is disabled.                                                   |
      |                                   |                                                                           |
      |                                   | -  **Pending deletion**                                                   |
      |                                   |                                                                           |
      |                                   |    The CMK is scheduled for deletion.                                     |
      |                                   |                                                                           |
      |                                   | -  **Pending import**                                                     |
      |                                   |                                                                           |
      |                                   |    If your CMK does not have materials, its status is **Pending import**. |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Created                           | Creation time of the CMK                                                  |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Key Algorithm and Usage           | Key algorithm selected during key creation and its usage                  |
      +-----------------------------------+---------------------------------------------------------------------------+
      | Origin                            | Source of key material, which can be one of the following:                |
      |                                   |                                                                           |
      |                                   | -  **External**                                                           |
      |                                   |                                                                           |
      |                                   |    The key is imported to the KMS from an external system.                |
      |                                   |                                                                           |
      |                                   | -  **Key Management Service**                                             |
      |                                   |                                                                           |
      |                                   |    The key is a default key or created in KMS.                            |
      +-----------------------------------+---------------------------------------------------------------------------+

5. You can click the key alias to view its details.

   .. note::

      To change the alias or description of the CMK, click |image3| next to the value of **Name** or **Description**.

      -  A default key (the alias suffix of which is **/default**) does not allow name and description changes.
      -  The name and description of a CMK cannot be changed if the CMK is in **Pending deletion** status.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002479637644.png
.. |image3| image:: /_static/images/en-us_image_0231665754.png
