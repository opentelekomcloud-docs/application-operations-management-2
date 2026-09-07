:original_name: mon_01_00234.html

.. _mon_01_00234:

(New) Setting Filters for AOM Dashboards
========================================

Add filters to new AOM dashboards to filter statistical graphs based on specified conditions. Filters are used to modify query criteria for statistical graphs in new dashboards in batches. Each statistical graph is actually the results of a query and analysis statement.

AOM supports the following types of filters:

-  Custom variable: You can set static or dynamic variable values and use them in query statements for batch statement modification. In this way, you can filter statistical graphs based on custom variables.

Configuring a Filter of the Custom Variable Type
------------------------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Dashboard** > **Dashboard**. Click **Try New Version** in the upper right corner of the page.

#. Click a dashboard to go to its details page.

#. Click |image1| in the upper right corner of the dashboard details page. The **Dashboard Settings** page is displayed.

#. Click **Create**. On the page that is displayed, set parameters for the filter of the custom variable type.

   a. Configure a filter of the custom variable type by referring to the following table.

      .. table:: **Table 1** Basic information

         +-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter   | Description                                                                                                                                                                                                                                          |
         +=============+======================================================================================================================================================================================================================================================+
         | Name        | Name of a filter. Each name must be unique. Enter up to 255 characters and do not start or end with an underscore (_). Only digits, letters, and underscores are allowed.                                                                            |
         +-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Alias       | (Optional) Alias of the filter. Enter up to 255 characters and do not start or end with an underscore (_) or hyphens (-). Only digits, letters, hyphens, and underscores are allowed. After the filter alias is set, it is displayed preferentially. |
         +-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description | (Optional) Description of the filter. Enter up to 1,000 characters.                                                                                                                                                                                  |
         +-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Type        | Type of the filter. Select **Custom variable**. You can set static or dynamic variable values and use them in query statements for batch statement modification.                                                                                     |
         +-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. .. _mon_01_00234__li1380173116416:

      (Optional) Configure a static variable value for the filter of the custom variable type.

      #. Click **Add Static Variable Value** in the **Static Variable Value** area.

      #. Configure a static variable by referring to the following table.

         .. table:: **Table 2** Static variable configuration

            +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                         | Description                                                                                                                                                                                                                                                                                        |
            +===================================+====================================================================================================================================================================================================================================================================================================+
            | Value                             | Field value of the static variable. Enter up to 255 characters and do not start or end with an underscore (_). Only digits, letters, and underscores are allowed.                                                                                                                                  |
            +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Alias                             | (Optional) Alias of the field value of the static variable. Enter up to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. Do not start with a period or underscore or end with a period. After an alias is set, it will be displayed preferentially. |
            +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Default Value                     | Whether to use the value of the static variable as the default value. (If an alias has been set, the alias will be displayed preferentially.):                                                                                                                                                     |
            |                                   |                                                                                                                                                                                                                                                                                                    |
            |                                   | -  Enable: The value of the static variable is automatically selected as the default value of the filter.                                                                                                                                                                                          |
            |                                   | -  Disable: The value of the static variable is not automatically selected as the default value of the filter.                                                                                                                                                                                     |
            +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

         To delete a static variable value, click **Delete** in the **Operation** column.

   c. .. _mon_01_00234__li158036314412:

      (Optional) Configure a dynamic variable value for the filter of the custom variable type.

      #. Toggle on **Dynamic Variable Value**.
      #. Configure the source of the dynamic variable value:

         -  **Prometheus instance**: Query dynamic variable values from a Prometheus instance.

      #. Configure dynamic variable parameters.

         -  When **Dynamic Variable Value Source** is set to **Prometheus instance**, set parameters by referring to the following table.

            .. table:: **Table 3** Dynamic variable configuration (source: Prometheus instance)

               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Parameter                         | Description                                                                                                                                                                                                                                                              |
               +===================================+==========================================================================================================================================================================================================================================================================+
               | Prometheus instance               | Prometheus instance from which dynamic variable values are queried. By default, the Prometheus instance selected in the upper left corner after you access the dashboard details page is used. This parameter is grayed here and cannot be selected.                     |
               |                                   |                                                                                                                                                                                                                                                                          |
               |                                   | To change the Prometheus instance, select another Prometheus instance on the dashboard details page.                                                                                                                                                                     |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Query Method                      | Option: **Metric field match**.                                                                                                                                                                                                                                          |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Metric Name                       | Select a metric under the selected Prometheus instance.                                                                                                                                                                                                                  |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Variable Display Field            | Select a field of the metric to display. The values corresponding to this field will be displayed in the dashboard filter drop-down list.                                                                                                                                |
               |                                   |                                                                                                                                                                                                                                                                          |
               |                                   | Example: If this parameter is set to **Cluster Name**, specific cluster names will be displayed in the dashboard filter drop-down list.                                                                                                                                  |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Variable Value Field              | Select an actual field for filtering.                                                                                                                                                                                                                                    |
               |                                   |                                                                                                                                                                                                                                                                          |
               |                                   | For example, if **Variable Display Field** is set to **Cluster Name** and **Variable Value Field** is set to **Cluster ID**, when you select a cluster name from the dashboard filter drop-down list, the actual cluster ID will be used as the criterion for filtering. |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Filter Criteria                   | Configure a dimension name and value. The **=** and **!=** operators are supported.                                                                                                                                                                                      |
               |                                   |                                                                                                                                                                                                                                                                          |
               |                                   | You can click |image2| to use **AND** to set multiple filter criteria for the same metric.                                                                                                                                                                               |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
               | Sort By                           | Configure how the options will be displayed in the dashboard filter drop-down list. Option: **None**.                                                                                                                                                                    |
               +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Configure other information about the filter of the custom variable type.

      -  **Default Value**: Configure the default value of the filter. You can select the static or dynamic variable values configured in :ref:`2 <mon_01_00234__li1380173116416>` or :ref:`3 <mon_01_00234__li158036314412>`.
      -  **Multi-Option Allowed**: Whether multiple options can be selected for the filter. This function is enabled by default. After this function is enabled, multiple options are selectable for the filter.
      -  **Include "Select All"**: Whether the **Select All** option is available in the drop-down list. This function is enabled by default. After this function is enabled, the **Select All** option is selectable.

   e. Click **Preview** to preview your filter settings.

#. Click **OK** to create a filter of the custom variable type.

   The new filter is displayed on the dashboard details page and the page for adding a graph. You can click the filter and enter a criterion in the search box or select a criterion from the drop-down list to filter statistical graphs in a dashboard.

More Operations
---------------

After a filter is created, perform the operations listed in :ref:`Table 4 <mon_01_00234__table5594143619592>` on the **Dashboard Settings** page if needed.

.. _mon_01_00234__table5594143619592:

.. table:: **Table 4** More operations

   +---------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                         | Description                                                                                                                                                                                                                                                                                                                               |
   +===================================================+===========================================================================================================================================================================================================================================================================================================================================+
   | Searching for a filter                            | Search for filters by name, alias, type, or description. Enter or select a keyword in the search box above the filter list and click |image3| to search.                                                                                                                                                                                  |
   +---------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Editing a filter                                  | Click **Modify** in the **Operation** column that contains the target filter.                                                                                                                                                                                                                                                             |
   +---------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting a filter                                 | Click **Delete** in the **Operation** column that contains the target filter. In the dialog box that is displayed, click **Yes**.                                                                                                                                                                                                         |
   +---------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Using a filter to fill in a dashboard graph title | After a filter is added, use *${Filter name}* to dynamically fill in a dashboard :ref:`graph title <mon_01_0209__table1325112581810>`. (If an alias has been configured for the filter, it will be used preferentially.) The graph title can then be dynamically displayed based on the filter drop-down list values.                     |
   |                                                   |                                                                                                                                                                                                                                                                                                                                           |
   |                                                   | For example, if the original graph name is **Dashboard** and the new filter is *ClusterName*, you can set the dashboard graph name to **$**\ *{ClusterName}* **Dashboard**. Then, select values from the drop-down list of **ClusterName**. These values will be dynamically combined with the original dashboard graph name for display. |
   +---------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002337031712.png
.. |image2| image:: /_static/images/en-us_image_0000002337031716.png
.. |image3| image:: /_static/images/en-us_image_0000002370949917.png
