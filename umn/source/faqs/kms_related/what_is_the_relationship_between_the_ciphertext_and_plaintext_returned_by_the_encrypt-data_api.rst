:original_name: kms_01_0215.html

.. _kms_01_0215:

What Is the Relationship Between the Ciphertext and Plaintext Returned by the encrypt-data API?
===============================================================================================

The basic length of the ciphertext returned by the encrypt-data API is 124 bytes. The ciphertext consists of multiple fields, including the key ID, encryption algorithm, key version, and ciphertext digest.

The plaintext has 16 bytes in each block. A block with fewer than 16 bytes will be padded. Ciphertext length = 124 + Ceil(plaintext length/16) x 16. The conversion result is encoded using Base64.

Take 4-byte plaintext input as an example. The calculation result is 124 + Ceil(4/16) x 16 = 140. The 140 bytes are converted into 188 bytes after Base64 encoding.

.. note::

   Ceil is a round-up function. Ceil(a) = 1. The value range of **a** is (0,1].
