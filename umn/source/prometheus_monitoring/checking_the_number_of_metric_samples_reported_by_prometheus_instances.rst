:original_name: mon_01_0125.html

.. _mon_01_0125:

Checking the Number of Metric Samples Reported by Prometheus Instances
======================================================================

After metric data is reported to AOM through Prometheus monitoring, you can view the number of basic and custom metric samples reported by Prometheus instances.

Prerequisites
-------------

-  Your service has been connected for Prometheus monitoring. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.

Constraints
-----------

-  Metric samples are reported every hour. If you specify a time range shorter than one hour, the query result of total metric samples may be 0.
-  The number of metric samples displayed on the **Usage Statistics** page may be different from the actual number.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Prometheus Monitoring** > **Usage Statistics**.
#. In the upper left corner of the page, select a desired Prometheus instance.
#. In the upper right corner of the page, set filter criteria.

   a. Set a time range. You can use a predefined time label, such as **Last hour** and **Last 6 hours**, or customize a time range. Max.: 30 days.

      You are advised to select a time range longer than 1 hour.

   b. Set the interval for refreshing information. Click the drop-down arrow next to |image1| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.

#. View the number of basic metrics and that of custom metrics reported by the Prometheus instance.

   -  **Custom Metric Samples**: include the number of custom metric samples reported within 24 hours and that reported within a specified time range.
   -  **Basic Metric Samples**: include the number of basic metric samples reported within 24 hours and that reported within a specified time range.
   -  **Custom Metrics**: indicates the number of custom metric types reported within a specified time range.
   -  **Basic Metrics**: indicates the number of basic metric types reported within a specified time range.
   -  **Top 10 Custom Metric Samples**: displays the top 10 custom metric samples within a specified time range.

#. In the **Instance Info** area, view **Total Custom Metric Samples (Million)**, **Total Basic Metric Samples (Million)**, **Custom Metric Samples in 24 Hours (Million)**, **Basic Metric Samples in 24 Hours (Million)**, **Custom Metrics**, and **Basic Metrics**.

.. |image1| image:: /_static/images/en-us_image_0000002336871632.png
