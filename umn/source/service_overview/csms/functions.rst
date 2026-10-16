:original_name: dew_01_9997.html

.. _dew_01_9997:

Functions
=========

CSMS is a secure, reliable, and easy-to-use secret hosting service. Users or applications can use CSMS to create, retrieve, update, and delete credentials in a unified manner throughout the secret lifecycle. CSMS can help you eliminate risks incurred by hardcoding, plaintext configuration, and permission abuse.

Unified Secret Management
-------------------------

Applications and business systems have a large number of secrets and are difficult to manage.

CSMS can store, retrieve, and use secrets in a unified manner throughout their lifecycles.

Perform the following operations to manage secrets using CSMS:

#. Collect secrets.
#. Upload the secrets to CSMS.

Secure Secret Retrieval
-----------------------

Many applications store plaintext secrets, such as passwords, tokens, certificates, SSH keys, and API keys, in their configuration files to be used for authentication when they access databases or other services. Plaintext and hardcoded secrets are prone to breach and incur security risks.

CSMS allows users to dynamically query secrets via APIs instead of hardcoding the secrets, greatly reducing breach risks.

Perform the following operations to manage secrets using CSMS:

When an application reads its configurations, it calls CSMS APIs to retrieve secrets. Neither hardcoded nor plaintext secrets are required.

Secret Event Notification
-------------------------

After you subscribe to an associated event for a secret object, if the event is enabled and a basic event is triggered on the secret object, an event notification is sent to the notification topic specified by the event through Simple Message Notification (SMN). Basic event types include new secret version creation, secret version expiration, secret deletion, and secret rotation. After configuring event notification, you can use event-driven managed functions in FunctionGraph to automatically rotate secrets.

Perform the following operations to manage secrets using CSMS:

1. The administrator adds an event on the CSMS event notification console or by calling the API.

2. When creating or updating a secret, you need to associate the event object required for subscription.

3. You will receive an event notification when the secret status changes. You can configure functions in FunctionGraph to automatically update or rotate secrets.

CSMS Basic Functions
--------------------

.. table:: **Table 1** CSMS basic functions

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Function                          | Description                                                                                                                      |
   +===================================+==================================================================================================================================+
   | Secret lifecycle management       | -  Create, view, immediately delete, back up, and restore secrets, as well as scheduling and canceling the deletion of a secret. |
   |                                   | -  Change the secret encryption key and description.                                                                             |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Secret version management         | -  Create and view secret versions.                                                                                              |
   |                                   | -  View secret values.                                                                                                           |
   |                                   | -  Set secret version expiration configurations.                                                                                 |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Secret version status management  | Update, query, and delete secret versions.                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Secret tag management             | Add, search for, edit, and delete tags.                                                                                          |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Secret event management           | -  Create, view, and delete events                                                                                               |
   |                                   | -  Secret change event types                                                                                                     |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
