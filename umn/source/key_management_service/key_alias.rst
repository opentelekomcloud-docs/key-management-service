:original_name: en-us_topic_0000001891946490.html

.. _en-us_topic_0000001891946490:

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
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| on the left and choose **Security** > **Key Management Service**.
#. Click the target key name. On the key details page, click the **Alias** tab.
#. Click **Create Alias**. Enter the alias in the displayed dialog box and click **OK**.

   .. note::

      Only digits, letters, underscores (_), hyphens (-), colons (:), and slashes (/) are allowed.

Deleting an Alias
-----------------

#. Log in to the management console.
#. Click |image3| in the upper left corner of the management console and select a region or project.
#. Click |image4| on the left and choose **Security** > **Key Management Service**.
#. Click the target key name. On the key details page, click the **Alias** tab.
#. Locate the target alias and click **Delete** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0000001284811084.png
.. |image2| image:: /_static/images/en-us_image_0000002511598459.png
.. |image3| image:: /_static/images/en-us_image_0000001284811084.png
.. |image4| image:: /_static/images/en-us_image_0000002479645998.png
