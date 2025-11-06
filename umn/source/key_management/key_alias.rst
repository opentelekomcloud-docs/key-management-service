:original_name: en-us_topic_0000002203211100.html

.. _en-us_topic_0000002203211100:

Key Alias
=========

An alias is an identifier of a key. You can use the alias as the key ID during API calling. The original key alias is not used as the key name.

This section describes how to add and delete an alias for a key.

Constraints
-----------

-  An alias can be used for only one key. A key can has multiple aliases.
-  The aliases are unique in a region but can be the same in different regions.
-  The aliases cannot be modified once being created.
-  A maximum of 50 aliases can be created for a key.

Creating an Alias
-----------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region or project.
#. Choose **Security** > **Key Management Service** .
#. Click the target key name. On the key details page, click the **Alias** tab.
#. Click **Create Alias**. Enter the alias in the displayed dialog box and click **OK**.

   .. note::

      Only digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/) are allowed.

Deleting an Alias
-----------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region or project.
#. Choose **Security** > **Key Management Service** .
#. Click the target key name. On the key details page, click the **Alias** tab.
#. Enter **DELETE** in the confirmation dialog box and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002203676060.png
.. |image2| image:: /_static/images/en-us_image_0000002238636017.png
