:original_name: kms_01_0033.html

.. _kms_01_0033:

Changing the Alias and Description of a CMK
===========================================

Scenario
--------

The alias of a CMK is a user-friendly name designed to help you locate the CMK easier.

This section describes how to change the alias and description of a CMK on the KMS management console.

.. important::

   -  A Default Master Key (the alias suffix of which is **/default**) does not allow alias and description changes.
   -  The alias and description of a CMK cannot be changed if the CMK is in **Pending deletion** status.

Prerequisites
-------------

-  The CMK is in **Enabled**, **Disabled**, or **Pending import** status.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the alias of the desired CMK. Details about the CMK are displayed.

#. To change the alias or description of the CMK, click |image2| next to the value of **Alias** or **Description**.


   .. figure:: /_static/images/en-us_image_0129270877.png
      :alt: **Figure 1** CMK details

      **Figure 1** CMK details

   .. note::

      -  The alias must be 1 to 255 characters in length. Only digits, letters, underscores (_), hyphens (-), colons (:), and forward slashes (/) are allowed.
      -  Length of the description cannot exceed 255 characters.

#. Click |image3| to save the changes.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
.. |image2| image:: /_static/images/en-us_image_0237809858.png
.. |image3| image:: /_static/images/en-us_image_0237809856.png
