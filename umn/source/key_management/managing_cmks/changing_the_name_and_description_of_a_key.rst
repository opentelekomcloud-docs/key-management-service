:original_name: kms_01_0033.html

.. _kms_01_0033:

Changing the Name and Description of a Key
==========================================

Scenario
--------

Key names help you find custom keys more easily.

This section describes how to change the name and description of a custom key on the KMS management console.

.. important::

   -  The name and description of the default master key cannot be modified. The name of the default master key ends with **/default**.
   -  The name and description of a key cannot be changed if the key is in **Pending deletion** status.

Prerequisites
-------------

-  The custom key is in **Enabled**, **Disabled**, or **Pending import** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the name or description of the target key to access its details page.

#. To change the alias or description of a key, click |image2| next to **Name** or **Description**.


   .. figure:: /_static/images/en-us_image_0000002172643144.png
      :alt: **Figure 1** Key details

      **Figure 1** Key details

   .. note::

      -  The name can contain 1 to 255 characters. Only digits, letters, underscores (_), hyphens (-), colons (:), and forward slashes (/) are allowed.
      -  Length of the description cannot exceed 255 characters.

#. Click |image3| to save the changes.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0237809858.png
.. |image3| image:: /_static/images/en-us_image_0237809856.png
