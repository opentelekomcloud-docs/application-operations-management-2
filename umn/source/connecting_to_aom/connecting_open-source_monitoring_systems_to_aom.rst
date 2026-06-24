:original_name: mon_01_0070.html

.. _mon_01_0070:

Connecting Open-Source Monitoring Systems to AOM
================================================

AOM provides a unified entry for observability analysis of cloud services. Through the access center, you can create a common Prometheus instance to connect open-source monitoring systems to AOM.

Scenario
--------

This type of instance is recommended when Prometheus servers have been built. The availability and scalability of Prometheus storage need to be ensured through remote write.

Creating a Common Prometheus Instance
-------------------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, create a common Prometheus instance through either of the following entries:

   -  Entry 1:

      a. Choose **Access Center** > **Access Center**. The **Access Center** page is displayed. (To switch from the new access center to the old one, click **Back to Old Version** in the upper right corner.)
      b. In the **Open-Source Monitoring** panel, click the **Common Prometheus instance** card.

   -  Entry 2:

      Choose **Prometheus Monitoring** > **Instances** and click **Add Prometheus Instance**.

#. In the displayed dialog box, set an instance name, enterprise project, and instance type.

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
      | Instance Type                     | Type of the Prometheus instance. Select **Common Prometheus Instance**.                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
