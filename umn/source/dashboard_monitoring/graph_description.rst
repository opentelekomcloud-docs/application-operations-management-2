:original_name: mon_01_0048.html

.. _mon_01_0048:

Graph Description
=================

The dashboard displays the query and analysis results of metric data in graphs (such as line/digit/status graphs).

.. _mon_01_0048__section781281957:

Metric Data Graphs
------------------

Metric data graphs support the following types: :ref:`line <mon_01_0048__li1648711268149>`, :ref:`number <mon_01_0048__li151831949141410>`, :ref:`top N <mon_01_0048__li16687125313110>`, :ref:`table <mon_01_0048__li126341111163219>`, :ref:`bar <mon_01_0048__li163252512211>`, and :ref:`digital line <mon_01_0048__li263365204216>` graphs.

-  .. _mon_01_0048__li1648711268149:

   **Line graph**: used to analyze the data change trend in a certain period. Use this type of graph when you need to monitor the metric data trend of one or more resources within a period.

   You can use a line graph to compare the same metric of different resources. The following figure shows the CPU usage of different hosts.


   .. figure:: /_static/images/en-us_image_0000002336871384.png
      :alt: **Figure 1** Line graph

      **Figure 1** Line graph

   .. table:: **Table 1** Line graph parameters

      +-------------------+--------------------+--------------------------------------------------------------------------------+
      | Category          | Parameter          | Description                                                                    |
      +===================+====================+================================================================================+
      | ``-``             | X Axis Title       | Title of the X axis.                                                           |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Y Axis Title       | Title of the Y axis.                                                           |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Fit as Curve       | Whether to fit a smooth curve.                                                 |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Hide X Axis Label  | Whether to hide the X axis label.                                              |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Hide Y Axis Label  | Whether to hide the Y axis label.                                              |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Display Background | If this option is enabled, the background will be displayed in the line graph. |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Y Axis Range       | Value range of the Y axis.                                                     |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      | Advanced Settings | Left Margin        | Distance between the axis and the left boundary of the graph.                  |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Right Margin       | Distance between the axis and the right boundary of the graph.                 |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Top Margin         | Distance between the axis and the upper boundary of the graph.                 |
      +-------------------+--------------------+--------------------------------------------------------------------------------+
      |                   | Bottom Margin      | Distance between the axis and the lower boundary of the graph.                 |
      +-------------------+--------------------+--------------------------------------------------------------------------------+

-  .. _mon_01_0048__li151831949141410:

   **Digit graph**: highlights a single value. It can display the latest value and the growth or decrease rate of a resource in a specified period. Use this type of graph to monitor the latest value of a metric in real time.

   As shown in the following figure, you can view the CPU usage of the host in real time. **2.85%** indicates the latest CPU usage, and **-0.08%** indicates the decrease rate in the current monitoring period.


   .. figure:: /_static/images/en-us_image_0000002336871440.png
      :alt: **Figure 2** Digit graph

      **Figure 2** Digit graph

   .. table:: **Table 2** Digit graph parameters

      +----------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                                             |
      +================+=========================================================================================================================+
      | Show Miniature | After this function is enabled, the icon will be zoomed out based on a certain proportion. Also, a line graph is added. |
      +----------------+-------------------------------------------------------------------------------------------------------------------------+

-  .. _mon_01_0048__li16687125313110:

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

-  .. _mon_01_0048__li126341111163219:

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

-  .. _mon_01_0048__li163252512211:

   **Bar graph**: A vertical or horizontal bar graph compares values between categories. It shows the data of different categories and counts the number of elements in each category. You can also draw multiple rectangles for the same type of attributes. Grouping and cascading modes are available so that you can analyze data from different dimensions.

   In the following figure, you can view the CPU usage of different hosts in a graph.


   .. figure:: /_static/images/en-us_image_0000002336871368.png
      :alt: **Figure 5** Bar graph

      **Figure 5** Bar graph

   .. table:: **Table 5** Bar graph parameters

      +-------------------+-------------------+----------------------------------------------------------------+
      | Category          | Parameter         | Description                                                    |
      +===================+===================+================================================================+
      | ``-``             | X Axis Title      | Title of the X axis.                                           |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Y Axis Title      | Title of the Y axis.                                           |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Hide X Axis Label | Whether to hide the X axis label.                              |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Hide Y Axis Label | Whether to hide the Y axis label.                              |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Y Axis Range      | Value range of the Y axis.                                     |
      +-------------------+-------------------+----------------------------------------------------------------+
      | Advanced Settings | Left Margin       | Distance between the axis and the left boundary of the graph.  |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Right Margin      | Distance between the axis and the right boundary of the graph. |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Top Margin        | Distance between the axis and the upper boundary of the graph. |
      +-------------------+-------------------+----------------------------------------------------------------+
      |                   | Bottom Margin     | Distance between the axis and the lower boundary of the graph. |
      +-------------------+-------------------+----------------------------------------------------------------+

-  .. _mon_01_0048__li263365204216:

   **Digital line graph**: a trend analysis graph. It shows the change of a group of ordered data (usually in a continuous time interval) and intuitively displays related data analysis. It can display the latest data and the growth or decrease rate of the resource in a specified monitoring period. Use this type of graph when you need to monitor the metric data trend of one or more resources within a period.

   As shown in the following figure, the CPU usages in different periods are displayed in the same graph. **2.93%** indicates the latest CPU usage, and **0.00%** indicates the growth rate of the CPU usage in the current monitoring period.


   .. figure:: /_static/images/en-us_image_0000002370949353.png
      :alt: **Figure 6** Digital line graph

      **Figure 6** Digital line graph

   .. table:: **Table 6** Digital line graph parameters

      =========================== ===========================================
      Parameter                   Description
      =========================== ===========================================
      Fit as Curve                Whether to fit a smooth curve.
      Show Legend                 Whether to display legends.
      Hide X Axis Label           Whether to hide the X axis label.
      Hide Y Axis Background Line Whether to hide the Y axis background line.
      Show Data Markers           Whether to display the connection points.
      =========================== ===========================================
