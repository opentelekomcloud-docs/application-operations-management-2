:original_name: mon_01_0026.html

.. _mon_01_0026:

Observability Metric Browsing
=============================

The **Metric Browsing** page displays metric data of each resource. You can monitor metric values and trends in real time, and create alarm rules for real-time service data monitoring and analysis.

Monitoring Metrics
------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Metric Browsing**.

#. Select a target Prometheus instance from the drop-down list.

#. Select one or more metrics from all metrics or by running Prometheus statements. For details about how to set monitoring conditions, see :ref:`Table 2 <mon_01_0003__table108101311715>`.

   -  Select metrics from all metrics.

      After selecting a target metric, you can set condition attributes to filter information.

      You can click **Add Metric** to add metrics and set information such as statistical period for the metrics. You can perform the following operations after moving the cursor to the metric data and monitoring condition:

      -  Click |image1| next to a monitoring condition to hide the corresponding metric data record in the graph.
      -  Click |image2| next to a monitoring condition to convert the metric data and monitoring condition into a Prometheus command.
      -  Click |image3| next to a monitoring condition to quickly copy the metric data and monitoring condition and modify them as required.
      -  Click |image4| next to a monitoring condition to remove a metric data record from monitoring.

   -  Select metrics by running Prometheus statements. For details about Prometheus statements, see :ref:`Prometheus Statements <mon_01_0043>`.

#. Set metric parameters by referring to :ref:`Table 1 <mon_01_0026__table2478253172013>`, view the metric graph in the upper part of the page, and analyze metric data from multiple perspectives.

   .. _mon_01_0026__table2478253172013:

   .. table:: **Table 1** Metric parameters

      +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                                            |
      +===================+========================================================================================================================================================================+
      | Statistic         | Method used to measure metrics. Options: **Avg**, **Min**, **Max**, **Sum**, and **Samples**. **Samples**: the number of data points.                                  |
      +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Time Range        | Time range in which metric data is collected. Options: **Last 30 minutes**, **Last hour**, **Last 6 hours**, **Last day**, **Last week**, and **Custom**.              |
      +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Refresh Frequency | Interval at which the metric data is refreshed. Options: **Refresh manually**, **30 seconds auto refresh**, **1 minute auto refresh**, and **5 minutes auto refresh**. |
      +-------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. (Optional) Set the display layout of metric data.

   On the right of the page, click the down arrow, select a desired graph type from the drop-down list, and set graph parameters (such as the X axis title, Y axis title, and displayed value). For details about the parameters, see :ref:`Metric Data Graphs <mon_01_0048__section781281957>`. **Up to 200 metric data records can be displayed in a line graph.**

Related Operations
------------------

You can also perform the operations listed in :ref:`Table 2 <mon_01_0026__table18762012174619>`.

.. _mon_01_0026__table18762012174619:

.. table:: **Table 2** Related operations

   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                            | Description                                                                                                                                                                                                                                                                                                                                             |
   +======================================+=========================================================================================================================================================================================================================================================================================================================================================+
   | Adding an alarm rule for a metric    | After selecting a metric, click |image8| in the upper right corner of the metric list to add an alarm rule for the metric. **When you are redirected to the** **Create Alarm Rule** **page, your settings made on the** **Metric Browsing** **page will be automatically applied to** **Alarm Rule Settings** **and** **Alarm Rule Details** **areas.** |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting a metric                    | Click |image9| next to the target metric.                                                                                                                                                                                                                                                                                                               |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Adding a metric graph to a dashboard | After selecting a metric, click |image10| in the upper right corner of the metric list.                                                                                                                                                                                                                                                                 |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371030409.png
.. |image2| image:: /_static/images/en-us_image_0000002370950269.png
.. |image3| image:: /_static/images/en-us_image_0000002370950265.png
.. |image4| image:: /_static/images/en-us_image_0000002337032072.png
.. |image5| image:: /_static/images/en-us_image_0000002337032064.png
.. |image6| image:: /_static/images/en-us_image_0000002336872320.png
.. |image7| image:: /_static/images/en-us_image_0000002337032052.png
.. |image8| image:: /_static/images/en-us_image_0000002337032064.png
.. |image9| image:: /_static/images/en-us_image_0000002336872320.png
.. |image10| image:: /_static/images/en-us_image_0000002337032052.png
