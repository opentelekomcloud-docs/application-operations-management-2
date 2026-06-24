:original_name: mon_01_0210.html

.. _mon_01_0210:

(New) Graphs
============

Dashboard graphs show the query and analysis results of metrics.

.. _mon_01_0210__section3839184316536:

Metric Data Graphs
------------------

The following types of graphs are supported: :ref:`line graphs <mon_01_0210__li1648711268149>`, :ref:`digit graphs <mon_01_0210__li151831949141410>`, :ref:`top N graphs <mon_01_0210__li16687125313110>`, :ref:`tables <mon_01_0210__li126341111163219>`, :ref:`bars <mon_01_0210__li163252512211>`, and :ref:`digital line graphs <mon_01_0210__li263365204216>`.

-  .. _mon_01_0210__li1648711268149:

   **Line graph**: used to analyze the data change trend in a certain period. Use this type of graph when you need to monitor the metric data trend of one or more resources within a period.

   You can use a line graph to compare the same metric of different resources. The following figure shows the CPU usage of different hosts.


   .. figure:: /_static/images/en-us_image_0000002371030525.png
      :alt: **Figure 1** Line graph

      **Figure 1** Line graph

   .. table:: **Table 1** Line graph parameters

      +----------+--------------------+--------------------------------------------------------------------------------+
      | Category | Parameter          | Description                                                                    |
      +==========+====================+================================================================================+
      | Graphics | Line Shape         | Line type. Options: **Straight** and **Curved**.                               |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Display Background | If this option is enabled, the background will be displayed in the line graph. |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Top Margin         | Distance between the axis and the upper boundary of the graph.                 |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Bottom Margin      | Distance between the axis and the lower boundary of the graph.                 |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Left Margin        | Distance between the axis and the left boundary of the graph.                  |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Right Margin       | Distance between the axis and the right boundary of the graph.                 |
      +----------+--------------------+--------------------------------------------------------------------------------+
      | X Axis   | Show               | Whether to display the X axis.                                                 |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | X Axis Title       | Title of the X axis.                                                           |
      +----------+--------------------+--------------------------------------------------------------------------------+
      | Y Axis   | Show               | Whether to display the Y axis.                                                 |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Y Axis Title       | Title of the Y axis.                                                           |
      +----------+--------------------+--------------------------------------------------------------------------------+
      |          | Y Axis Range       | Value range of the Y axis.                                                     |
      +----------+--------------------+--------------------------------------------------------------------------------+

-  .. _mon_01_0210__li151831949141410:

   **Digit Graph**: used to highlight a single value. Use this type of graph to monitor the latest value of a metric in real time.

   In the following figure, you can view the CPU usage of a host in real time.


   .. figure:: /_static/images/en-us_image_0000002337032172.png
      :alt: **Figure 2** Digit graph

      **Figure 2** Digit graph

   .. table:: **Table 2** Digit graph parameters

      +----------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                                             |
      +================+=========================================================================================================================+
      | Show Miniature | After this function is enabled, the icon will be zoomed out based on a certain proportion. Also, a line graph is added. |
      +----------------+-------------------------------------------------------------------------------------------------------------------------+

-  .. _mon_01_0210__li16687125313110:

   **Top N**: The statistical unit is a cluster and statistical objects are resources such as hosts, components, or instances in the cluster. The top N graph displays top N resources in a cluster. By default, top 5 resources are displayed.

   To view the top N resources, add a top N graph to the dashboard. You only need to select resources and metrics, for example, host CPU usage. AOM then automatically singles out top N hosts for display. If the number of resources is less than N, actual resources are displayed.

   In the following graph, the top 5 hosts with the highest CPU usage are displayed.


   .. figure:: /_static/images/en-us_image_0000002337031116.png
      :alt: **Figure 3** Top N graph

      **Figure 3** Top N graph

   .. table:: **Table 3** Top N graph parameters

      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      | Category          | Parameter            | Description                                                                            |
      +===================+======================+========================================================================================+
      | ``-``             | Sorting Order        | Sorting order of data. Default: **Descending**.                                        |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Upper Limit          | The maximum number of resources to be displayed in the top N graph. Default: **5**.    |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Dimension            | Metric dimensions to be displayed in the top N graph.                                  |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Column Width         | Column width. Options: **auto** (default), **16**, **22**, **32**, **48**, and **60**. |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Unit                 | Unit of the data to be displayed. Default: **%**.                                      |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Display X-Axis Scale | After this function is enabled, the scale of the X axis is displayed.                  |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Show Value           | After this function is enabled, the value on the Y axis is displayed.                  |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Display Y-Axis Line  | After this function is enabled, the line on the Y axis is displayed.                   |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      | Advanced Settings | Left Margin          | Distance between the axis and the left boundary of the graph.                          |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Right Margin         | Distance between the axis and the right boundary of the graph.                         |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Top Margin           | Distance between the axis and the upper boundary of the graph.                         |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+
      |                   | Bottom Margin        | Distance between the axis and the lower boundary of the graph.                         |
      +-------------------+----------------------+----------------------------------------------------------------------------------------+

-  .. _mon_01_0210__li126341111163219:

   **Table**: A table lists content in a systematic, concise, centralized, and comparative manner, and intuitively shows the relationship between different categories or makes comparison, ensuring accurate display of data.

   In the following figure, you can view the CPU usage of different hosts in a table.


   .. figure:: /_static/images/en-us_image_0000002370949409.png
      :alt: **Figure 4** Table

      **Figure 4** Table

   .. table:: **Table 4** Table parameters

      ============ ===========================================
      Parameter    Description
      ============ ===========================================
      Field Name   Name of a field.
      Field Rename Rename a table header field when necessary.
      ============ ===========================================

-  .. _mon_01_0210__li163252512211:

   **Bar graph**: A vertical or horizontal bar graph compares values between categories. It shows the data of different categories and counts the number of elements in each category. You can also draw multiple rectangles for the same type of attributes. Grouping and cascading modes are available so that you can analyze data from different dimensions.

   In the following figure, you can view the CPU usage of different hosts in a graph.


   .. figure:: /_static/images/en-us_image_0000002337032164.png
      :alt: **Figure 5** Bar graph

      **Figure 5** Bar graph

   .. table:: **Table 5** Bar graph parameters

      +----------+---------------+----------------------------------------------------------------+
      | Category | Parameter     | Description                                                    |
      +==========+===============+================================================================+
      | Graphics | Top Margin    | Distance between the axis and the upper boundary of the graph. |
      +----------+---------------+----------------------------------------------------------------+
      |          | Bottom Margin | Distance between the axis and the lower boundary of the graph. |
      +----------+---------------+----------------------------------------------------------------+
      |          | Left Margin   | Distance between the axis and the left boundary of the graph.  |
      +----------+---------------+----------------------------------------------------------------+
      |          | Right Margin  | Distance between the axis and the right boundary of the graph. |
      +----------+---------------+----------------------------------------------------------------+
      | X Axis   | Show          | Whether to display the X axis.                                 |
      +----------+---------------+----------------------------------------------------------------+
      |          | X Axis Title  | Title of the X axis.                                           |
      +----------+---------------+----------------------------------------------------------------+
      | Y Axis   | Show          | Whether to display the Y axis.                                 |
      +----------+---------------+----------------------------------------------------------------+
      |          | Y Axis Title  | Title of the Y axis.                                           |
      +----------+---------------+----------------------------------------------------------------+
      |          | Y Axis Range  | Value range of the Y axis.                                     |
      +----------+---------------+----------------------------------------------------------------+

-  .. _mon_01_0210__li263365204216:

   **Digital line graph**: used to analyze the data change trend in a certain period and intuitively display related data. Use this type of graph when you need to monitor the metric data trend of one or more resources within a period.

   In the following figure, you can view the CPU usage in different periods in a graph.


   .. figure:: /_static/images/en-us_image_0000002337032168.png
      :alt: **Figure 6** Digital line graph

      **Figure 6** Digital line graph

   .. table:: **Table 6** Digital line graph parameters

      +------------+-------------------+--------------------------------------------------+
      | Category   | Parameter         | Description                                      |
      +============+===================+==================================================+
      | Chart Mode | Line Shape        | Line type. Options: **Straight** and **Curved**. |
      +------------+-------------------+--------------------------------------------------+
      |            | Hide Legend       | Whether to hide legends.                         |
      +------------+-------------------+--------------------------------------------------+
      |            | Show              | Whether to display the X axis.                   |
      +------------+-------------------+--------------------------------------------------+
      |            | Show              | Whether to display the Y axis.                   |
      +------------+-------------------+--------------------------------------------------+
      |            | Show Data Markers | Whether to display the connection points.        |
      +------------+-------------------+--------------------------------------------------+
