:original_name: kms_01_0024.html

.. _kms_01_0024:

Adding a Tag
============

Tags are used to identify keys. You can add tags to custom keys so that you can classify custom keys, trace them, and collect their usage status according to the tags.

Constraints
-----------

Tags cannot be added to default keys.

Procedure
---------

#. Log in to the management console.

#. Click |image1|. Choose **Security** > **Key Management Service**. The **Key Management Service** page is displayed.

#. Click the alias of the target custom key to view its details.

#. Click **Tags** to go to the tag management page.

#. Click **Add Tag**. In the **Add Tag** dialog box, enter the tag key and tag value. :ref:`Table 1 <kms_01_0024__t2276fe27aa3d4e03a154c9332ff563f6>` describes the parameters.


   .. figure:: /_static/images/en-us_image_0000001677882901.png
      :alt: **Figure 1** Adding a tag

      **Figure 1** Adding a tag

   .. note::

      If you want to delete a tag to be added when adding multiple tags, you can click **Delete** in the row where the tag to be added is located to delete the tag.

   .. _kms_01_0024__t2276fe27aa3d4e03a154c9332ff563f6:

   .. table:: **Table 1** Tag parameters

      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+-----------------+
      | Parameter       | Description                                                                                                                                                        | Value                                                  | Example Value   |
      +=================+====================================================================================================================================================================+========================================================+=================+
      | Tag key         | Name of a tag.                                                                                                                                                     | -  Mandatory.                                          | cost            |
      |                 |                                                                                                                                                                    | -  The tag key must be unique for the same custom key. |                 |
      |                 | The same tag (including tag key and tag value) can be used for different custom keys. However, under the same custom key, one tag key can have only one tag value. | -  128 characters limit.                               |                 |
      |                 |                                                                                                                                                                    | -  The value cannot start or end with a space.         |                 |
      |                 | A maximum of 20 tags can be added for one custom key.                                                                                                              | -  The following character types are allowed:          |                 |
      |                 |                                                                                                                                                                    |                                                        |                 |
      |                 |                                                                                                                                                                    |    -  English                                          |                 |
      |                 |                                                                                                                                                                    |    -  Numbers                                          |                 |
      |                 |                                                                                                                                                                    |    -  Special characters: \_-@                         |                 |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+-----------------+
      | Tag value       | Value of the tag                                                                                                                                                   | -  This parameter can be empty.                        | 100             |
      |                 |                                                                                                                                                                    | -  255 characters limit.                               |                 |
      |                 |                                                                                                                                                                    | -  The following character types are allowed:          |                 |
      |                 |                                                                                                                                                                    |                                                        |                 |
      |                 |                                                                                                                                                                    |    -  English                                          |                 |
      |                 |                                                                                                                                                                    |    -  Numbers                                          |                 |
      |                 |                                                                                                                                                                    |    -  Special characters: \_-@                         |                 |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+-----------------+

#. Click **OK** to complete.

.. |image1| image:: /_static/images/en-us_image_0000001295227514.png
