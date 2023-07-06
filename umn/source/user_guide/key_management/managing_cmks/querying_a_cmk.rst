:original_name: kms_01_0096.html

.. _kms_01_0096:

Querying a CMK
==============

Scenario
--------

This section describes how to use the management console to view the information about a CMK, such as its alias, status, ID, and creation time. The status of a CMK can be **Enabled**, **Disabled**, **Pending deletion**, or **Pending import**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. In the CMK list you can view details about the CMKs.


   .. figure:: /_static/images/en-us_image_0129269716.png
      :alt: **Figure 1** CMK list

      **Figure 1** CMK list

   .. note::

      -  Select the CMK status from the drop-down list of **All statuses**. Then the CMK list displays only the CMKs in the corresponding state.
      -  Enter the alias of a CMK in the search box on top of the CMK list. Click |image2| or press Enter to search for the specified CMK.
      -  You can click **Search Tag** to search for the CMK that meets the search criteria.
      -  You can click |image3| at the upper right corner on top of the CMK list to show or hide columns of the CMK list.

   :ref:`Table 1 <kms_01_0096__table15653286125723>` describes the parameters of a CMK list.

   .. _kms_01_0096__table15653286125723:

   .. table:: **Table 1** CMK list parameters

      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                   |
      +===================================+===============================================================================================+
      | Alias                             | Alias of a CMK                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | Status                            | Status of a CMK, which can be one of the following:                                           |
      |                                   |                                                                                               |
      |                                   | -  **Enabled**                                                                                |
      |                                   |                                                                                               |
      |                                   |    The CMK is enabled.                                                                        |
      |                                   |                                                                                               |
      |                                   | -  **Disabled**                                                                               |
      |                                   |                                                                                               |
      |                                   |    The CMK is disabled.                                                                       |
      |                                   |                                                                                               |
      |                                   | -  **Pending deletion**                                                                       |
      |                                   |                                                                                               |
      |                                   |    The CMK is scheduled for deletion.                                                         |
      |                                   |                                                                                               |
      |                                   | -  **Pending import**                                                                         |
      |                                   |                                                                                               |
      |                                   |    If your CMK does not have the key material, its status is **Pending import**.              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | ID                                | Random ID of a CMK generated during the CMK creation                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | Creation Time                     | Creation time of the CMK                                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | Expiration Time                   | Expiration time of the key material. When the material expires, the CMK becomes an empty CMK. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+
      | Origin                            | Source of key material, which can be one of the following:                                    |
      |                                   |                                                                                               |
      |                                   | -  **External**                                                                               |
      |                                   |                                                                                               |
      |                                   |    You import the key material for the CMK.                                                   |
      |                                   |                                                                                               |
      |                                   | -  Key Management Service                                                                     |
      |                                   |                                                                                               |
      |                                   |    The CMK uses KMS-generated material.                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------+

#. You can click the alias of a CMK to view its details.


   .. figure:: /_static/images/en-us_image_0129270434.png
      :alt: **Figure 2** Viewing CMK details

      **Figure 2** Viewing CMK details

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0237809855.png
.. |image3| image:: /_static/images/en-us_image_0237809857.png
