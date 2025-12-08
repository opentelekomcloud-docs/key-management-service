:original_name: dew_01_0222.html

.. _dew_01_0222:

Personal Data Protection Mechanism
==================================

To ensure that your personal data, such as the username, password, and mobile phone number, will not be leaked or obtained by unauthorized or unauthenticated entities or people, DEW controls access to the data and records logs for operations performed on the data.

Personal Data to Be Collected
-----------------------------

:ref:`Table 1 <dew_01_0222__table5267747204311>` lists the personal data generated or collected by DEW.

.. _dew_01_0222__table5267747204311:

.. table:: **Table 1** Personal data

   +-----------------+--------------------------------------------------------------------------+-----------------+-----------------+
   | Type            | Source                                                                   | Can Be Modified | Mandatory       |
   +=================+==========================================================================+=================+=================+
   | Tenant ID       | -  Tenant ID in the token when an operation is performed on the console. | No              | Yes             |
   |                 | -  Tenant ID in the token when an API is invoked.                        |                 |                 |
   +-----------------+--------------------------------------------------------------------------+-----------------+-----------------+

Storage Mode
------------

Tenant IDs are not sensitive data and are stored in plaintext.

Access Permission Control
-------------------------

Users can view only logs related to their own services.

Log Records
-----------

DEW records logs for all operations, such as editing, querying, and deleting, performed on personal data. The logs are uploaded to Cloud Trace Service (CTS). You can view only the logs generated for operations you performed.
