:original_name: mon_01_0206.html

.. _mon_01_0206:

Managing Metric and Log Ingestion
=================================

After ingesting metrics to AOM and logs to LTS in the access center, you can manage ingestion rules on the **Access Management** page.

Constraints
-----------

-  AOM provides both old and new access management functions. To switch from the :ref:`old function <mon_01_0198>` to the new function, click **Try New Version** in the upper right corner of the **Access Center** page and then go to the **Access Management** page.

-  To use LTS functions on the AOM console, obtain the LTS permissions in advance. For details, see `Permissions <https://docs.otc.t-systems.com/usermanual/lts/lts-03205.html>`__.
-  To use the log ingestion rule function on the AOM 2.0 console, enable LTS first.

Managing Metric Ingestion Rules
-------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Access Center** > **Access Management**. The **Metric Ingestion Rules** tab page is displayed.

#. Click **Ingest Metric**. In the dialog box, select a target card. For details, see :ref:`AOM Access Overview <mon_01_0196>`.

#. After the ingestion is complete, check the rule on the **Metric Ingestion Rules** tab page under **Access Management**.

   Perform the operations listed in :ref:`Table 1 <mon_01_0206__table152391347144912>` if needed.

   .. _mon_01_0206__table152391347144912:

   .. table:: **Table 1** Related operations

      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                                     | Description                                                                                                                                                                                  |
      +===============================================+==============================================================================================================================================================================================+
      | Searching for a metric ingestion rule         | Search for metric ingestion rules by **Ingestion Configuration**, **Ingestion Type**, or **Status** in the search box. Alternatively, enter a keyword to search for a metric ingestion rule. |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Refreshing the metric ingestion rules list    | Click |image1| in the upper right corner of the list to refresh current metric ingestion rules.                                                                                              |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Setting the metric ingestion rule list        | Click |image2| in the upper right corner of the list. In the displayed dialog box, customize column display.                                                                                 |
      |                                               |                                                                                                                                                                                              |
      |                                               | -  Basic settings                                                                                                                                                                            |
      |                                               |                                                                                                                                                                                              |
      |                                               |    -  **Table Text Wrapping**: If you enable this function, excess text will move down to the next line; otherwise, the text will be truncated.                                              |
      |                                               |    -  **Operation Column**: If you enable this function, the **Operation** column is always fixed at the rightmost position of the table.                                                    |
      |                                               |                                                                                                                                                                                              |
      |                                               | -  **Custom Columns**: Select or deselect the columns to display.                                                                                                                            |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Editing a metric ingestion rule               | Click **Edit** in the **Operation** column to modify a metric ingestion rule. For details, see :ref:`AOM Access Overview <mon_01_0196>`.                                                     |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a metric ingestion rule              | -  To delete a metric ingestion rule, click **Delete** in the **Operation** column.                                                                                                          |
      |                                               | -  To delete one or more metric ingestion rules, select them and click **Delete** above the list.                                                                                            |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enabling or disabling a metric ingestion rule | -  Enable or disable the rule in the **Status** column.                                                                                                                                      |
      |                                               | -  To enable or disable one or more rules, select them and click **Enable** or **Disable** above the list.                                                                                   |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Viewing the associated Prometheus instance    | Click an instance in the **Instance Name** column to go to the instance details page.                                                                                                        |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Managing Log Ingestion Rules
----------------------------

AOM is a unified platform for observability analysis of cloud services. It does not provide log functions by itself. Instead, it integrates the log ingestion rule function of Log Tank Service (LTS). You can perform operations on the AOM 2.0 or LTS console.

.. table:: **Table 2** Description

   +---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+
   | Function            | Description                                                                                                                                                                                 | AOM 2.0 Console                                                                          | LTS Console                                                                                 | References                                                                         |
   +=====================+=============================================================================================================================================================================================+==========================================================================================+=============================================================================================+====================================================================================+
   | Log ingestion rules | Logs can be ingested through ICAgents, cloud services, APIs, and SDKs. After logs are ingested, they are displayed in a simple and orderly manner on the console and can be queried easily. | #. Log in to the AOM 2.0 console.                                                        | #. Log in to the LTS console.                                                               | `Log Ingestion <https://docs.otc.t-systems.com/usermanual/lts/lts_02_0030.html>`__ |
   |                     |                                                                                                                                                                                             | #. In the navigation pane on the left, choose **Access Center** > **Access Management**. | #. In the navigation pane on the left, choose **Log Ingestion** > **Ingestion Management**. |                                                                                    |
   |                     |                                                                                                                                                                                             | #. Click the **Log Ingestion Rules** tab.                                                |                                                                                             |                                                                                    |
   +---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371030353.png
.. |image2| image:: /_static/images/en-us_image_0000002337031992.png
