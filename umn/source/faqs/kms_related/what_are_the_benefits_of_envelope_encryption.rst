:original_name: kms_01_0054.html

.. _kms_01_0054:

What Are the Benefits of Envelope Encryption?
=============================================

Envelope encryption is the practice of encrypting data with a DEK and then encrypting the DEK with a root key that you can fully manage. In this case, CMKs are not required for encryption or decryption.

Benefits:

-  Advantages over CMK encryption in KMS

   Users can use CMKs to encrypt and decrypt data on the KMS console or by calling KMS APIs.

   A CMK can encrypt and decrypt data no more than 4 KB. An envelope can encrypt and decrypt larger volumes of data.

   Data encrypted using envelopes does not need to be transferred. Only the DEKs need to be transferred to the KMS server.

-  Advantages over encryption by using cloud services

   -  Security

      Data transferred to the cloud for encryption is exposed to risks such as interception and phishing.

      During envelope encryption, KMS uses Hardware Security Modules (HSMs) to protect keys. All CMKs are protected by root keys in HSMs to avoid key leakage.

   -  Trustworthiness

      You will worry about data security on the cloud. It is also difficult for cloud services to prove that they never misuse or disclose such data.

      If you choose envelope encryption, KMS will control access to keys and record all usages of and operations on keys with traceable logs, meeting your audit and regulatory compliance requirements.

   -  Performance and cost

      To encrypt or decrypt data using a cloud service, you have to send the data to the encryption server and receive the processed data. This process seriously affects your service performance and incurs high costs.

      Envelope encryption allows you to generate DEKs online by calling KMS cryptographic algorithm APIs, and to encrypt a large amount of local data with the DEKs.
