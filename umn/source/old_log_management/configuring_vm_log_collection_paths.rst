:original_name: mon_01_0108.html

.. _mon_01_0108:

Configuring VM Log Collection Paths
===================================

AOM can collect and display VM logs. A VM refers to an Elastic Cloud Server (ECS) running Linux. Before collecting logs, ensure that you have set a log collection path.

Prerequisites
-------------

You need to install an ICAgent on your VM. About five minutes after the ICAgent is installed, you can view your VM in the VM list on the **Log Analysis** > **Log Paths** page.

Constraints
-----------

-  An ICAgent collects **\*.log**, **\*.trace**, and **\*.out** log files only. For example, **/opt/yilu/work/xig/debug_cpu.log**.
-  Ensure that an absolute path of a log directory or file is configured and the path exists. For example, **/opt/yilu/work/xig** or **/opt/yilu/work/xig/debug_cpu.log**.
-  The ICAgent does not collect log files from subdirectories. For example, the ICAgent does not collect log files from the **/opt/yilu/work/xig/debug** subdirectory of **/opt/yilu/work/xig**.
-  A maximum of 20 log collection paths can be configured for a VM.
-  For ECSs in the same resource space, only the latest log collection configuration in the system will be used. AOM and LTS log collection configurations cannot take effect at the same time. For example, if you configure log collection paths in AOM for ECSs, the previous collection configurations you made in LTS for these ECSs become invalid.

Configuring Log Collection Paths
--------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Log Management** > **Log Management**. On the displayed page, click **Old Edition** in the upper right corner.

#. On the **Log Paths** tab page, click |image1| in the **Operation** column of the target host to configure one or more log collection paths.

   You can use the paths automatically identified by the ICAgent or manually configure paths.

   -  **Using the Paths Automatically Identified by the ICAgent**

      The ICAgent automatically scans the log files of your VM, and displays all the **.log**, **.trace**, or **.out** log files with handles and their paths on the page.

      You can click |image2| in the **Operation** column to add a path automatically identified by the ICAgent to the configured log collection path list. To configure multiple paths, repeat this operation.

   -  **Manual configuration**

      If the paths automatically identified by ICAgent cannot meet your requirements, specify a log directory or file in the **Collection Path** text box. For example, enter **/usr/local/uniagentd/log/agent.log** and then add it to the configured log collection path list. To configure multiple paths, repeat this operation.

#. Click **Confirm**.

Viewing VM Logs
---------------

After the log collection paths are configured, the ICAgent collects log files from them. This operation takes about 1 minute to complete. After collecting logs, you can perform the following operations:

-  **Viewing VM Log Files**

   In the navigation pane, choose **Log Management** > **Log Files**. Click the **Host** tab to view the collected log files. For details, see :ref:`Checking Log Files <mon_01_0107>`.

-  **Viewing and Analyzing VM logs**

   In the navigation pane, choose **Log Management** > **Log Search**. Click the **Host** tab to view and analyze the collected logs by time range, keyword, and context. For details, see :ref:`Searching for Logs <mon_01_0106>`.

.. |image1| image:: /_static/images/en-us_image_0000002337031624.png
.. |image2| image:: /_static/images/en-us_image_0000002336871884.png
