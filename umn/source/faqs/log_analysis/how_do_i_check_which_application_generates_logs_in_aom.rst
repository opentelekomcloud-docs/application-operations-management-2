:original_name: aom_06_0037.html

.. _aom_06_0037:

How Do I Check Which Application Generates Logs in AOM?
=======================================================

Symptom
-------

A large number of logs are generated everyday. How do I check which application generates specific logs?

Solution
--------

AOM does not show the applications to which logs belong. To view that, ingest all logs to LTS and use its resource statistics function.

Procedure:

#. Create a log group and stream for your application. For details, see section "Creating Log Groups and Log Streams" in *LTS User Guide*.
#. Log in to the LTS console and view detailed resource statistics of top 100 log groups or streams using the resource statistics function.
