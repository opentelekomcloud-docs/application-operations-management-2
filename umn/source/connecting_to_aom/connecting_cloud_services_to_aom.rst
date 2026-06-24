:original_name: mon_01_0067.html

.. _mon_01_0067:

Connecting Cloud Services to AOM
================================

AOM provides a unified entry for observability analysis of cloud services. Through the access center, you can connect cloud services to AOM. Cloud service metrics (such as CPU usage and memory usage) can then be reported to AOM.

To quickly connect cloud services to AOM, perform the following steps:

#. Create a Prometheus instance for cloud services. This instance is used to store collected data. For details, see :ref:`Creating a Prometheus Instance for Cloud Services <mon_01_0067__section1775653192818>`.
#. Connect cloud services to AOM. For details, see :ref:`Connecting Cloud Services to AOM <mon_01_0067__section19328924183711>`.
#. After cloud services are connected to AOM, their metrics can be reported to AOM. You can go to the :ref:`Metric Browsing <mon_01_0026>` page to monitor metrics.

Constraints
-----------

-  Only one Prometheus instance for cloud services can be created in an enterprise project.

.. _mon_01_0067__section1775653192818:

Creating a Prometheus Instance for Cloud Services
-------------------------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. On the displayed page, click **Add Prometheus Instance**.

#. .. _mon_01_0067__li31111426151910:

   Set an instance name, enterprise project, and instance type.

   .. table:: **Table 1** Parameters for creating a Prometheus instance

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                 |
      +===================================+=============================================================================================================================================================+
      | Instance Name                     | Prometheus instance name.                                                                                                                                   |
      |                                   |                                                                                                                                                             |
      |                                   | Enter a maximum of 100 characters and do not start or end with an underscore (_) or hyphen (-). Only letters, digits, underscores, and hyphens are allowed. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project.                                                                                                                                         |
      |                                   |                                                                                                                                                             |
      |                                   | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                            |
      |                                   | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                        |
      |                                   | -  To use the enterprise project function, contact engineers.                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instance Type                     | Type of the Prometheus instance. Select **Prometheus for Cloud Services**.                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. _mon_01_0067__section19328924183711:


Connecting Cloud Services to AOM
--------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, ingest cloud service metrics through either of the following entries:

   -  Entry 1:

      a. Choose **Access Center** > **Access Center**. The **Access Center** page is displayed. (To switch from the new access center to the old one, click **Back to Old Version** in the upper right corner.)
      b. Click the cloud service to be connected on the **Cloud Services** panel.

   -  Entry 2:

      a. .. _mon_01_0067__li17938742101613:

         Choose **Prometheus Monitoring** > **Instances** and then click a target Prometheus instance.

      b. In the **Unconnected Cloud Services** area, click the cloud service to be connected.

#. In the displayed dialog box, set information about the cloud service.

   .. _mon_01_0067__table349315547133:

   .. table:: **Table 2** Connecting a cloud service

      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                     | Description                                                                                                                                                                                                                                                                                                                                  |
      +===============================================+==============================================================================================================================================================================================================================================================================================================================================+
      | Select Prometheus Instance for Cloud Services | Select the :ref:`Prometheus instance <mon_01_0067__section1775653192818>` for metric ingestion.                                                                                                                                                                                                                                              |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               | -  Enterprise Project                                                                                                                                                                                                                                                                                                                        |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               |    -  Connecting cloud services on the **Cloud Service Connection** page of the Prometheus instance details page: By default, the enterprise project is the same as that selected during the :ref:`creation of the Prometheus instance for cloud services <mon_01_0067__li31111426151910>`. This option is grayed and cannot be changed.     |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               |    -  Connecting cloud services through the access center: Select a required enterprise project from the drop-down list.                                                                                                                                                                                                                     |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               |       If the existing enterprise projects cannot meet your requirements, create one.                                                                                                                                                                                                                                                         |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               | -  Prometheus Instance for Cloud Services                                                                                                                                                                                                                                                                                                    |
      |                                               |                                                                                                                                                                                                                                                                                                                                              |
      |                                               |    -  Connecting cloud services on the **Cloud Service Connection** page of the Prometheus instance details page: By default, the value of this parameter is set to the :ref:`target Prometheus instance <mon_01_0067__li17938742101613>` selected in :ref:`1 <mon_01_0067__li17938742101613>`. This option is grayed and cannot be changed. |
      |                                               |    -  Connecting cloud services through the access center: By default, the value of this parameter is the Prometheus instance for cloud services under your selected enterprise project. If there is no such a Prometheus instance, create one.                                                                                              |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Connect Cloud Service Tags                    | You can determine whether to add cloud service tags to metric dimensions. After this function is enabled, tags of cloud service resources will be added to metric dimensions. Tag changes will be synchronized every hour. If the existing tags cannot meet your requirements, click **Go to Tag Management Service (TMS)** to add tags.     |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Connect Now**.

Other Operations
----------------

You can also perform the operations listed in :ref:`Table 3 <mon_01_0067__en-us_topic_0169698491_table289773015816>` on the **Cloud Service Connection** page of the Prometheus instance for cloud services.

.. _mon_01_0067__en-us_topic_0169698491_table289773015816:

.. table:: **Table 3** Related operations

   +----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                                            | Description                                                                                                                                                                                                |
   +======================================================================+============================================================================================================================================================================================================+
   | Searching for cloud services                                         | On the **Cloud Service Connection** page, enter a keyword in the search box to search for a cloud service.                                                                                                 |
   +----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disconnecting cloud services                                         | On the **Cloud Service Connection** page, click a target cloud service. In the displayed dialog box, click **Disconnect Cloud Service**.                                                                   |
   +----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Checking or modifying tag configurations of connected cloud services | On the **Cloud Service Connection** page, click a cloud service under **Connected Cloud Services** to change cloud service tag settings. For details, see :ref:`Table 2 <mon_01_0067__table349315547133>`. |
   +----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
