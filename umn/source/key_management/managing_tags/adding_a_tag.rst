:original_name: kms_01_0024.html

.. _kms_01_0024:

Adding a Tag
============

Scenario
--------

Tags are used to identify custom keys. You can add tags to custom keys so that you can classify custom keys, trace them, and collect their usage status according to the tags.

Constraints
-----------

Tags cannot be added to default keys.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Choose **Security** > **Key Management Service** . The key management page is displayed.

#. Click the name of the target custom key to view its details.

#. Click **Tags** to go to the tag management page.


   .. figure:: /_static/images/en-us_image_0000002208066957.png
      :alt: **Figure 1** Managing tags

      **Figure 1** Managing tags

#. Click **Add Tag**. In the **Add Tag** dialog box, enter the tag key and tag value. :ref:`Table 1 <kms_01_0024__teaf23b4b14f841aaaa772e07bee5a20a>` describes the parameters.


   .. figure:: /_static/images/en-us_image_0000002208068029.png
      :alt: **Figure 2** Adding a Tag

      **Figure 2** Adding a Tag

   .. note::

      If you want to delete a tag to be added when adding multiple tags, you can click **Delete** in the row where the tag to be added is located to delete the tag.

   .. _kms_01_0024__teaf23b4b14f841aaaa772e07bee5a20a:

   .. table:: **Table 1** Tag parameters

      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+-----------------+
      | Parameter       | Description                                                                                                                                                 | Value                                                                  | Example Value   |
      +=================+=============================================================================================================================================================+========================================================================+=================+
      | Tag key         | Name of a tag.                                                                                                                                              | -  Mandatory.                                                          | cost            |
      |                 |                                                                                                                                                             | -  Each tag key must be unique under the same custom key.              |                 |
      |                 | The same tag (including tag key and tag value) can be used for different keys. However, under the same custom key, one tag key can have only one tag value. | -  Contains a maximum of 36 characters.                                |                 |
      |                 |                                                                                                                                                             | -  Only digits, letters, underscores (_), and hyphens (-) are allowed. |                 |
      |                 | A maximum of 20 tags can be added for one custom key.                                                                                                       |                                                                        |                 |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+-----------------+
      | Tag value       | Value of the tag                                                                                                                                            | -  This parameter can be empty.                                        | 100             |
      |                 |                                                                                                                                                             | -  Can contain a maximum of 43 characters.                             |                 |
      |                 |                                                                                                                                                             | -  Only digits, letters, underscores (_), and hyphens (-) are allowed. |                 |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+-----------------+

#. Click **OK** to complete.

.. |image1| image:: /_static/images/en-us_image_0237800345.png
