:original_name: aom_04_0027.html

.. _aom_04_0027:

Common Response Headers
=======================

A response usually contains the following headers:

.. table:: **Table 1** Response headers

   +----------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Name           | Description                                                                                                       | Example                       |
   +================+===================================================================================================================+===============================+
   | Date           | (Standard HTTP header) Time when a message is sent. This field complies with RFC822 definitions.                  | Mon, 12 Nov 2007 15:55:01 GMT |
   +----------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Server         | (Standard HTTP header) Software that a server uses to process the request.                                        | Apache                        |
   +----------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Content-Length | (Standard HTTP header) Length of the response body, which is represented by a decimal number and stored in bytes. | xxx                           |
   +----------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Content-Type   | (Standard HTTP header) Media type of the response body sent to the recipient.                                     | application/json              |
   +----------------+-------------------------------------------------------------------------------------------------------------------+-------------------------------+
