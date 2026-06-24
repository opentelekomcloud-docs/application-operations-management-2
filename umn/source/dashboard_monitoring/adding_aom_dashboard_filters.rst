:original_name: mon_01_0090.html

.. _mon_01_0090:

Adding AOM Dashboard Filters
============================

You can customize filters by adding variables to filter monitoring data when viewing or adding graphs on the **Dashboard** page.

Adding Variables
----------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Dashboard** > **Dashboard**. (To switch from the new dashboard to the old one, click **Back to Old Version** in the upper right corner.)

   To use the new dashboard function, choose **Dashboard** in the navigation pane and then click **Try New Version** in the upper right corner of the page. For details about the filters of the new dashboard, see :ref:`(New) Setting Filters for AOM Dashboards <mon_01_00234>`.

#. Select a desired dashboard and click |image1| in the upper right corner of the **Dashboard** page. The **Variable Settings** page is displayed.

#. Click **Add Variable** and set parameters by referring to :ref:`Table 1 <mon_01_0090__table1730711167518>`.

   .. _mon_01_0090__table1730711167518:

   .. table:: **Table 1** Parameters for adding variables

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                            |
      +=======================+========================================================================================================================================================================================================================================+
      | Variable Name         | Name of a variable. Enter up to 255 characters and do not start or end with an underscore (_). Only digits, letters, and underscores are allowed.                                                                                      |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Type of the variable. Only **Query** is supported.                                                                                                                                                                                     |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alias                 | Alias of the variable. Enter up to 255 characters and do not start or end with an underscore (_) or hyphens (-). Only digits, letters, hyphens, and underscores are allowed. If you set an alias, it will be preferentially displayed. |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description           | Description of the variable. Enter up to 1,024 characters.                                                                                                                                                                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Source           | Source of the data. Select a data source on the **Dashboard** page. It is dimmed here and cannot be selected. The default Prometheus instance is selected by default.                                                                  |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Refresh Mode          | Filter refresh mode. Only **On dashboard load** is supported, which means refreshing filters when your dashboard is refreshed.                                                                                                         |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Metric                | Name of a metric. You can select metrics of the selected Prometheus instance.                                                                                                                                                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Field         | Displayed in a filter drop-down list on a dashboard.                                                                                                                                                                                   |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Value                 | Value of the display field.                                                                                                                                                                                                            |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Conditions            | Dimension name and value. You can set multiple conditions for the same metric.                                                                                                                                                         |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allow multiple values | Whether multiple values can be selected. By default, this function is disabled. If it is enabled, you can select multiple values for your custom filter.                                                                               |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Include "All"         | Whether the **All** option is available. By default, this function is disabled. If it is enabled, the **All** option will be added for your custom filter.                                                                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save** to add the variable.

   The new variable will be displayed as a filter on the dashboard page and the page for adding a graph. You can click the filter and select a desired value from the drop-down list.

More Operations
---------------

After the variable is added, you can perform the operations listed in :ref:`Table 2 <mon_01_0090__table5594143619592>` if needed.

.. _mon_01_0090__table5594143619592:

.. table:: **Table 2** Related operations

   +-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                     | Description                                                                                                                                                                                                                                                                                                                                      |
   +===============================================+==================================================================================================================================================================================================================================================================================================================================================+
   | Searching for a variable                      | You can search for variables by name. Enter a keyword in the search box above the variable list and click |image2| to search.                                                                                                                                                                                                                    |
   +-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Editing a variable                            | Click |image3| in the **Operation** column of the target variable. For details, see :ref:`Table 1 <mon_01_0090__table1730711167518>`.                                                                                                                                                                                                            |
   +-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting a variable                           | Click |image4| in the **Operation** column of the target variable. In the displayed dialog box, click **Yes**.                                                                                                                                                                                                                                   |
   +-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Filling a dashboard graph name with variables | Dashboards support the function of filling graph names using variables. After variables are added, dashboard graph names can be filled using *${variable name}* during :ref:`graph name configuration <mon_01_0003__table108101311715>`. The graph name is dynamically displayed based on the variable value you select from the drop-down list. |
   |                                               |                                                                                                                                                                                                                                                                                                                                                  |
   |                                               | For example, if the original graph name is **Dashboard** and the new variable is *ClusterName*, you can set the dashboard graph name to **$**\ *{ClusterName}* **Dashboard**. Then, select values from the drop-down list of **ClusterName**. These values will be dynamically combined with the original dashboard graph name for display.      |
   +-----------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002370949165.png
.. |image2| image:: /_static/images/en-us_image_0000002371029285.png
.. |image3| image:: /_static/images/en-us_image_0000002337030960.png
.. |image4| image:: /_static/images/en-us_image_0000002337030952.png
