:original_name: mon_02_0136.html

.. _mon_02_0136:

Ingesting MySQL Metrics to AOM
==============================

Create a collection task and install MySQL Exporter to monitor MySQL metrics on a host.

Prerequisites
-------------

-  :ref:`The UniAgent has been installed <agent_01_0005>` and is running.
-  :ref:`A Prometheus instance for ECS has been created <mon_01_0072>`.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, ingest middleware metrics:

   -  Choose **Prometheus Monitoring** > **Instances**. Click a Prometheus instance for ECS. On the instance details page, choose **Access Center** and then click the **MySQL** card.

#. On the displayed page, set parameters by referring to the following table.

   .. table:: **Table 1** Parameters for configuring a collection task

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation             | Parameter             | Description                                                                                                                                                                                                      |
      +=======================+=======================+==================================================================================================================================================================================================================+
      | Select Instance       | Prometheus Instance   | Select a Prometheus instance for ECS to store collected data.                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | A collection task is associated with the Prometheus instance to mark and classify collected data. If no Prometheus instance is available, :ref:`create one <mon_01_0072>`.                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Set Plug-in           | OS                    | Operating system of the host. Only Linux is supported.                                                                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Collection Plug-in    | The default value is **MYSQL**.                                                                                                                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Plug-in Version       | Select a plug-in version. Plug-in versions that have not been released are dimmed and cannot be selected.                                                                                                        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Set Collection Task   | Collection Task Name  | Name of a collection task. Enter 1 to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Host                  | Click **Add Host**. On the **Add Host** page, select the host for configuring the collection task and installing Exporter.                                                                                       |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | -  Search for and select a host by the host name, IP address, or Agent status.                                                                                                                                   |
      |                       |                       | -  You can click |image1| in the upper right corner to deselect the selected host.                                                                                                                               |
      |                       |                       | -  Ensure that the UniAgent of the selected host is running. Otherwise, no data can be collected.                                                                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Metric Dimension      | Click |image2|. In the displayed dialog box, select **Built-in** or **Custom** to add a metric dimension.                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | -  Metric dimension name:                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       |    -  Built-in metric dimensions: **\_app**, **\_comp**, and **\_env** are available, which are used to identify applications, components, and environments, respectively.                                       |
      |                       |                       |    -  Custom metric dimension: Enter a metric dimension name. Each name can contain 1 to 64 characters. Only letters, digits, and underscores (_) are allowed. Each name must start with a letter or underscore. |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       |    For a host, each metric dimension name must be unique.                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | -  Metric dimension value: Enter the value of a metric dimension. This value can be duplicate but cannot be empty.                                                                                               |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       |    Each value can contain 1 to 128 characters. The following characters are not allowed: ``&|><$;'!-()``                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | Up to 10 dimensions can be added. For example, if the dimension name is **label1** and the dimension value is **label2**, **label1:"label2"** will be displayed.                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Advanced Settings     | Configure the following parameters:                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                  |
      |                       |                       | -  **Collection Period (s)**: O&M data collection period, in seconds. Options: **10s**, **30s**, and **60s** (default).                                                                                          |
      |                       |                       | -  **Timeout Period (s)**: the maximum time allowed for executing a collection task, in seconds. Options: **10s**, **30s**, and **60s** (default). The timeout period cannot exceed the collection period.       |
      |                       |                       | -  **Executor**: user who executes the collection task, that is, the user of the selected host. The default value is **root**. Currently, only the **root** user is supported.                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Set Exporter installation parameters and click **Install**. Click **View Log** to view Exporter installation logs.

   Exporter collects monitoring data and regulates the data provided for external systems through Prometheus monitoring.

   +----------------+----------------------------------------------------------------------+
   | Parameter      | Description                                                          |
   +================+======================================================================+
   | MySQL Username | Username of MySQL.                                                   |
   +----------------+----------------------------------------------------------------------+
   | MySQL Password | Password of MySQL.                                                   |
   +----------------+----------------------------------------------------------------------+
   | MySQL Address  | IP address and port number of MySQL, for example, **10.0.0.1:3306**. |
   +----------------+----------------------------------------------------------------------+

#. Click **Install** to connect the MySQL plug-in. In the new access center, the connected plug-in is displayed on the **Metric Ingestion Rules** tab page under **Access Center** > **Access Management**.

   You can perform the operations listed in the following table on collection tasks.

   .. table:: **Table 2** Related operations

      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                                   | Description                                                                                                                                     |
      +=============================================+=================================================================================================================================================+
      | Checking a collection task                  | Click **Edit** in the **Operation** column of the target collection task to view details.                                                       |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enabling or disabling a collection task     | -  To enable or disable a collection task, toggle on or off the switch in the **Status** column of the collection task.                         |
      |                                             | -  To enable or disable one or more collection tasks, select them and click **Enable** or **Disable** above the list.                           |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Searching for a collection task             | Set filter criteria or enter keywords to search for a collection task.                                                                          |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Editing a collection task                   | Click **Edit** in the **Operation** column of the target collection task. On the displayed page, edit parameters as required.                   |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a collection task                  | -  To delete a collection task, click **Delete** in the **Operation** column.                                                                   |
      |                                             | -  To delete one or more collection tasks, select them and click **Delete** above the list.                                                     |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Checking the associated Prometheus instance | Click an instance in the **Instance Name** column to go to the instance details page.                                                           |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Refreshing the collection task list         | Click |image3| in the upper right corner of the list to refresh current metric ingestion rules.                                                 |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Setting the collection task list            | Click |image4| in the upper right corner of the list. In the displayed dialog box, customize column display.                                    |
      |                                             |                                                                                                                                                 |
      |                                             | -  Basic settings                                                                                                                               |
      |                                             |                                                                                                                                                 |
      |                                             |    -  **Table Text Wrapping**: If you enable this function, excess text will move down to the next line; otherwise, the text will be truncated. |
      |                                             |    -  **Operation Column**: If you enable this function, the **Operation** column is always fixed at the rightmost position of the table.       |
      |                                             |                                                                                                                                                 |
      |                                             | -  **Custom Columns**: Select or deselect the columns to display.                                                                               |
      +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371029153.png
.. |image2| image:: /_static/images/en-us_image_0000002336871240.png
.. |image3| image:: /_static/images/en-us_image_0000002460961512.png
.. |image4| image:: /_static/images/en-us_image_0000002461121136.png
