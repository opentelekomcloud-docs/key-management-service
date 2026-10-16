:original_name: dew_01_0186.html

.. _dew_01_0186:

Why Can't I Wrap Asymmetric Keys by Using -id-aes256-wrap-pad in OpenSSL?
=========================================================================

Symptom
-------

By default, the -id-aes256-wrap-pad algorithm is not enabled in OpenSSL. To wrap a key, upgrade OpenSSL to the latest version and patch it first.

Solution
--------

Use bash commands to create a local copy of the existing OpenSSL. You do not need to delete or modify the default OpenSSL client installation configurations.

#. Switch to the **root** user.

   **sudo su -**

#. Run the following command and record the OpenSSL version:

   **openssl version**

#. Run the following commands to create the **/root/build** directory. This directory will be used to store the latest OpenSSL binary file.

   **mkdir $HOME/build**

   **mkdir -p $HOME/local/ssl**

   **cd $HOME/build**

#. .. _dew_01_0186__li831410228281:

   Download the latest OpenSSL version from https://www.openssl.org/source/.

#. Download and decompress the binary file.

#. Replace **openssl-1.1.1d.tar.gz** with the latest OpenSSL version downloaded in :ref:`step 4 <dew_01_0186__li831410228281>`.

   **curl -O https://www.openssl.org/source/openssl-1.1.1d.tar.gz**

   **tar -zxf openssl-1.1.1d.tar.gz**

#. Use the **gcc** tool to patch the version, and compile the downloaded binary file.

   **yum install patch make gcc -y**

   .. note::

      If you are using a version other than OpenSSL-1.1.1d, you may need to change the directory and commands used, or this patch may not work properly.

#. Run the following commands:

   .. code-block::

      sed -i "/BIO_get_cipher_ctx(benc, &ctx);/a\ EVP_CIPHER_CTX_set_flags(ctx, EVP_CIPHER_CTX_FLAG_WRAP_ALLOW);" $HOME/build/openssl-1.1.1d/apps/enc.c

#. Run the following commands to compile the OpenSSL **enc.c** file:

   **cd $HOME/build/openssl-1.1.1d/**

   **./config --prefix=$HOME/local --openssldir=$HOME/local/ssl**

   **make -j$(grep -c ^processor /proc/cpuinfo)**

   **make install**

#. Configure the environment variable **LD_LIBRARY_PATH** to ensure that required libraries are available for OpenSSL. The latest version of OpenSSL has been dynamically linked to the binary file in the **$HOME/local/ssl/lib/** directory, and cannot be directly executed in shell.

#. Create a script named **openssl.sh** to load the **$HOME/local/ssl/lib/** path before running the binary file.

   **cd $HOME/local/bin/**

   **echo -e '#!/bin/bash \\nenv LD_LIBRARY_PATH=$HOME/local/lib/ $HOME/local/bin/openssl "$@"' > ./openssl.sh**

#. Run the following command to configure an execute bit on the script:

   **chmod 755 ./openssl.sh**

#. Run the following command to start the patched OpenSSL version:

   **$HOME/local/bin/openssl.sh**
