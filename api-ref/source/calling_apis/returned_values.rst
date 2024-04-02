:original_name: kms_02_0056.html

.. _kms_02_0056:

Returned Values
===============

Status Code
-----------

After sending a request, you will receive a response containing the status code, response header, and response body.

A status code is a group of digits ranging from 1xx to 5xx. It indicates the status of a response. For more information, see :ref:`Status Code <kms_02_0301>`.

For example, if status code **201** is returned for calling the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, the request is successful.

Response Header
---------------

A response header corresponds to a request header, for example, **Content-Type**.

:ref:`Figure 1 <kms_02_0056__en-us_topic_0207581477_en-us_topic_0169294978_fig4865141011511>` shows the response header for the API of `obtaining a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, in which **x-subject-token** is the desired user token. Then, you can use the token to authenticate the calling of other APIs.

.. _kms_02_0056__en-us_topic_0207581477_en-us_topic_0169294978_fig4865141011511:

.. figure:: /_static/images/en-us_image_0218769431.png
   :alt: **Figure 1** Header of the response to the request for obtaining a user token

   **Figure 1** Header of the response to the request for obtaining a user token

(Optional) Response Body
------------------------

A response body is generally returned in a structured format, corresponding to the **Content-Type** in the response header, and is used to transfer content other than the response header.

The following shows part of the response body for the API to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. For the sake of space, only part of the content is displayed here.

.. code-block::

   {
       "token": {
           "expires_at": "2019-02-13T06:52:13.855000Z",
           "methods": [
               "password"
           ],
           "catalog": [
               {
                   "endpoints": [
                       {
                           "region_id": "xxxxxxxx",
   ......

If an error occurs during API calling, the system returns an error code and a message to you. The following shows the format of an error response body:

.. code-block::

   {
       "error": {
           "message": "The request you have made requires authentication.",
           "title": "Unauthorized"
       }
   }

In the preceding information, **error_code** is an error code, and **error_msg** describes the error.
