:original_name: dew_01_0227.html

.. _dew_01_0227:

How Does KMS Protect My Keys?
=============================

The mechanism of KMS prevents anyone from accessing your keys in plaintext. KMS relies on hardware security modules (HSMs) that safeguard the confidentiality and integrity of your keys. Plaintext KMS keys are always encrypted by HSMs and are never stored on any disk. These keys are only utilized within the volatile memory of the HSMs for as long as necessary to perform the cryptographic operation you have requested.
