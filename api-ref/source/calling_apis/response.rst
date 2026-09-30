:original_name: aom_04_0060.html

.. _aom_04_0060:

Response
========

Status Code
-----------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request. For more information, see :ref:`Status Codes <aom_04_0021>`.

If status code **201** is returned for the calling of the API for `obtaining a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

For the API used to obtain a user token, the **x-subject-token** header field is the desired user token. This token can then be used to authenticate the calling of other APIs.


.. figure:: /_static/images/en-us_image_0000002193024392.png
   :alt: **Figure 1** Header fields of the response to the request for obtaining a user token

   **Figure 1** Header fields of the response to the request for obtaining a user token

Response Body
-------------

The body of a response is often returned in structured format as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to obtain a user token.

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
                           "region_id": "xx-xxxxxx-1",
   ......

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "errorCode": "SVCSTG_AMS_4000001",
       "errorMessage": "Request param invalid"
   }

In the response body, **errorCode** is an error code, and **errorMessage** provides information about the error.
