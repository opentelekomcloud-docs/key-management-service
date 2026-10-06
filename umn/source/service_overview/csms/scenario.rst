:original_name: dew_01_9995.html

.. _dew_01_9995:

Scenario
========

This section uses a basic database username and its password as an example to describe how CSMS works.

The administrator saves and updates secret values. The user obtains the required secret value through third-party application services. For details, see :ref:`Figure 1 <dew_01_9995__fig4248029164015>`.

.. _dew_01_9995__fig4248029164015:

.. figure:: /_static/images/en-us_image_0000001245361692.png
   :alt: **Figure 1** Secret-based login process

   **Figure 1** Secret-based login process

The procedure is as follows:

#. .. _dew_01_9995__li1292317534256:

   Create a secret on the console or via an API to store database information (such as the database address, port, and password).

#. Use an application to access the database. CSMS will query the secret that the administrator created in :ref:`Step 1 <dew_01_9995__li1292317534256>`.

#. CSMS retrieves and decrypts the secret ciphertext, and securely returns the information stored in the secret to the application through the secret management API.

#. The application obtains the decrypted plaintext secret and uses it to access the database.
