:original_name: dew_01_8886.html

.. _dew_01_8886:

Adding a Tag
============

Tags are used to identify secrets. You can easily classify and track secrets using tags.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Click a secret name to go to the details page.

#. In the **Tags** area, click **Add Tag**, as shown in :ref:`Figure 1 <dew_01_8886__ff809bb6d608c464aa1430d54c02b19be>`. In the **Add Tag** dialog box, enter the tag key and tag value. :ref:`Table 1 <dew_01_8886__t2276fe27aa3d4e03a154c9332ff563f6>` describes the parameters.

   .. _dew_01_8886__ff809bb6d608c464aa1430d54c02b19be:

   .. figure:: /_static/images/en-us_image_0000002244405836.png
      :alt: **Figure 1** Adding a tag

      **Figure 1** Adding a tag

   .. note::

      -  To delete a tag, click **Delete** next to it.

   .. _dew_01_8886__t2276fe27aa3d4e03a154c9332ff563f6:

   .. table:: **Table 1** Tag parameters

      +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Parameter             | Description                                                                                        | Remarks                                                |
      +=======================+====================================================================================================+========================================================+
      | Tag key               | Tag name.                                                                                          | -  Mandatory.                                          |
      |                       |                                                                                                    | -  The tag key must be unique for the same custom key. |
      |                       | The tag keys of a secret cannot have duplicate values. A tag key can be used for multiple secrets. | -  128 characters limit.                               |
      |                       |                                                                                                    | -  The value cannot start or end with a space.         |
      |                       | A secret can have up to 20 tags.                                                                   | -  The following character types are allowed:          |
      |                       |                                                                                                    |                                                        |
      |                       |                                                                                                    |    -  English                                          |
      |                       |                                                                                                    |    -  Numbers                                          |
      |                       |                                                                                                    |    -  Special characters: \_-                          |
      +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Tag value             | Value of the tag                                                                                   | -  Optional                                            |
      |                       |                                                                                                    | -  255 characters limit.                               |
      |                       |                                                                                                    | -  The following character types are allowed:          |
      |                       |                                                                                                    |                                                        |
      |                       |                                                                                                    |    -  English                                          |
      |                       |                                                                                                    |    -  Numbers                                          |
      |                       |                                                                                                    |    -  Special characters: \_-                          |
      +-----------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
