:original_name: dew_01_8882.html

.. _dew_01_8882:

Saving and Viewing Secret Values
================================

This section describes how to save and view secret values on the CSMS console.

You can create a new version of a secret to encrypt and keep a new secret value. By default, the latest secret version in **SYSCURRENT** state. The previous version is in the **SYSPREVIOUS** state.

Constraints
-----------

-  A secret can have up to 20 versions.
-  Secret versions are numbered v1, v2, v3, and so on based on their creation time.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| on the left and choose **Security** > **Data Encryption Workshop**.

#. In the navigation pane on the left, choose **Cloud Secret Management Service** > **Secrets**.

#. Click a secret name to go to the details page.

#. In the **Current Version** area, click **Add Secret Version**. In the displayed dialog box, enter the secret key/value or plaintext secret.


   .. figure:: /_static/images/en-us_image_0000002279577861.png
      :alt: **Figure 1** Adding a secret value

      **Figure 1** Adding a secret value

#. You can select an expiration time for the stored secret value. The time can be specific to seconds. After the setting is complete, you can view the expiration time in the secret version list. For example, Jun 30, 2023 19:52:59.

#. Click **OK**. A message is displayed in the upper right corner of the page, indicating that the value is added successfully.

#. In the **Version List** area, locate the target secret version, click **View Secret** in the **Operation** column, as shown in :ref:`Figure 2 <dew_01_8882__fig12640530968>`.

   .. _dew_01_8882__fig12640530968:

   .. figure:: /_static/images/en-us_image_0000002279465617.png
      :alt: **Figure 2** Secret version list

      **Figure 2** Secret version list

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001122737100.png
.. |image2| image:: /_static/images/en-us_image_0000002195596772.png
