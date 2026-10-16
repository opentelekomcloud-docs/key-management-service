:original_name: dew_01_9996.html

.. _dew_01_9996:

Advantages
==========

Secret Encryption
-----------------

Secrets are encrypted by KMS before storage. Encryption keys are generated and protected by authenticated third-party HSM. When you retrieve secrets, they are transferred to local servers via TLS.

Secure Secret Retrieval
-----------------------

CSMS calls secret APIs instead of hard-coded secrets in applications. Secrets can be dynamically retrieved and managed. CSMS manages application secrets in a centralized manner to reduce breach risks.

Secret Change Notification
--------------------------

SMN notifies users of basic secret event changes in a timely manner. FunctionGraph is used to configure functions to automatically update or rotate secrets.
