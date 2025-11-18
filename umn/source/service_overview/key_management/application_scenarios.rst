:original_name: kms_01_0046.html

.. _kms_01_0046:

Application Scenarios
=====================

KMS can manage CMKs used for data encryption and decryption in Object Storage Service (OBS), Elastic Volume Service (EVS), Image Management Service (IMS), Scalable File Service (SFS), Relational Database Service (RDS), and user applications.

-  For OBS, KMS applies to object encryption on OBS.

   .. note::

      OBS is an object-based storage service that provides customers with massive, secure, reliable, and cost-effective data storage capabilities, including but not limited to bucket creation, modification, deletion, and management, as well as object upload, download, deletion, and general management. OBS can store all file types, and is suitable for individual subscribers, websites, enterprises, and developers. For details about OBS, see *Object Storage Service (OBS) User Guide*.

-  For EVS, KMS applies to data encryption in EVS disks.

   .. note::

      Based on a distributed architecture, an EVS disk is a virtual block storage device that can be elastically scaled up and down. EVS disks can be operated online. Using them is the same as using common server hard disks. Compared with traditional hard disks, EVS disks have higher data reliability and I/O throughput and are easier to use. EVS disks can be used in file systems, databases, and system software applications that require block storage devices. For more information about EVS, see the *Elastic Volume Service User Guide*.

-  For IMS, KMS applies to the creation of encrypted private images.

   .. note::

      IMS provides easy-to-use self-service image management functions. You can apply for a cloud server using either a private image or a public image. You can also create a private image using an existing ECS or an external image file. For more information about IMS, see the *Image Management Service User Guide*.

-  For SFS, KMS applies to data encryption for files in SFS.

   .. note::

      SFS provides high-performance file storage that is scalable on demand. It can be shared with multiple cloud servers. For more information, see the *Scalable File Service User Guide*.

-  For RDS, KMS applies to disk encryption in RDS database instances.

   .. note::

      RDS is an online relational database service based on the cloud computing platform. RDS is out-of-box, reliable, scalable, and easy to manage. For more information about RDS, see the *Relational Database Service User Guide*.

-  For user applications

   To encrypt plaintext data, a user application can call the necessary KMS API to generate a DEK, which can then be used to encrypt the plaintext data. Then the application can store the encrypted data. In addition, the user application can call the necessary KMS APIs to create custom keys. DEKs can be stored in ciphertext after being encrypted with the custom keys. :ref:`Figure 1 <kms_01_0046__fig30019918195516>` shows envelope encryption working principles.

   To ensure the security of the user's encrypted data, KMS does not save DEKs in plaintext or ciphertext. Instead, it manages users' custom keys so that users can obtain and use DEKs securely.

   .. _kms_01_0046__fig30019918195516:

   .. figure:: /_static/images/en-us_image_0112946996.png
      :alt: **Figure 1** Envelope encryption working principles

      **Figure 1** Envelope encryption working principles
