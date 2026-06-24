:original_name: agent_01_00272.html

.. _agent_01_00272:

Connecting Custom Plug-ins to AOM
=================================

Create a plug-in, specify the metrics to be reported to AOM using a script, and create a collection task. Then the specified metrics can be reported to AOM for monitoring.

Prerequisites
-------------

-  :ref:`The UniAgent has been installed <agent_01_0005>` and is running.
-  :ref:`A Prometheus instance for ECS has been created <mon_01_0072>`.

Creating a Custom Plug-in
-------------------------

You can create a plug-in using a custom script and create a collection task :ref:`during the connection of the custom plug-in <agent_01_00272__agent_01_0027_section59610573377>` to report metrics to AOM.

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center** to go to the old access center. (The new access center does not support the connection of custom plug-ins. To switch from the new access center to the old one, click **Back to Old Version** in the upper right corner.)

#. In the **Custom Prometheus Plug-in Access** panel, click **Custom Plug-in**.

#. On the displayed page, set related parameters.

   -  Plug-in information

      .. table:: **Table 1** Plug-in parameters

         +--------------+-------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter    | Description                                                                                                                               |
         +==============+===========================================================================================================================================+
         | Plug-in Name | Name of a custom plug-in. Enter a maximum of 32 characters starting with a letter. Only letters, digits, and underscores (_) are allowed. |
         +--------------+-------------------------------------------------------------------------------------------------------------------------------------------+
         | Plug-in Type | Type of a plug-in. The default value is **Custom**.                                                                                       |
         +--------------+-------------------------------------------------------------------------------------------------------------------------------------------+
         | Description  | Description of the plug-in to be created. Enter a maximum of 20,000 characters.                                                           |
         +--------------+-------------------------------------------------------------------------------------------------------------------------------------------+

   -  .. _agent_01_00272__agent_01_0027_en-us_topic_0000001875791466_li164767163242:

      Set Plug-in

      .. table:: **Table 2** Plug-in configuration parameters

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                          |
         +===================================+======================================================================================================================================================================================================================================================================================+
         | Plug-in Version                   | Version of the custom plug-in.                                                                                                                                                                                                                                                       |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Plug-in Script                    | Custom plug-in script. You need to specify the metrics to be reported to AOM in this script. The script type can be **Linux** or **Windows**.                                                                                                                                        |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | **Linux**: Shell or Python script.                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | Example:                                                                                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | .. code-block::                                                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   |    #!/bin/bash                                                                                                                                                                                                                                                                       |
         |                                   |    #Examples                                                                                                                                                                                                                                                                         |
         |                                   |    echo "metric_name{label_name=\"label_value\"} 100"                                                                                                                                                                                                                                |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | **Windows**: BAT script                                                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | Example:                                                                                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | .. code-block::                                                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   |    ::Examples                                                                                                                                                                                                                                                                        |
         |                                   |    @echo off                                                                                                                                                                                                                                                                         |
         |                                   |    echo metric_name{label_name="label_value"} 100                                                                                                                                                                                                                                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Default Script Parameter          | Default parameters of the custom plug-in script. Set default parameters for script modeling. You can also leave them empty. Rules:                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | **$**\ *{Parameter}*: Enter a maximum of 64 characters starting with a letter. Only letters, digits, and underscores (_) are allowed. For example, **${a_b}**.                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | You can combine parameters as required and separate them with spaces. Max.: 250 characters. For example, **${a} ${b}**.                                                                                                                                                              |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Script Parameter                  | Configure the attributes of the default parameters in the custom plug-in script. You can configure the following information as required:                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | -  **Mandatory**: If this option is enabled, the parameter value in the plug-in debugging area is mandatory. If this option is disabled, the parameter value in the plug-in debugging area is optional.                                                                              |
         |                                   | -  **Parameter**: name of a script parameter. The system automatically identifies the script parameter name based on **Default Script Parameter** you have already configured. The parameter here is grayed and cannot be configured.                                                |
         |                                   | -  **Default Value**: default value of the script parameter.                                                                                                                                                                                                                         |
         |                                   | -  **Description**: description of the parameter.                                                                                                                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                                                                                      |
         |                                   | When you :ref:`configure a collection task <agent_01_00272__agent_01_0027_li2966194183215>` for the custom plug-in, script parameters are displayed based on the script parameter attributes configured here. You can configure collection based on the script parameter attributes. |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save**.

   After a plug-in is created, you can modify it, create a version for it, or delete it.

   .. table:: **Table 3** Related operations

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================+
      | Checking the plug-in status       | Locate the target plug-in, hover the mouse pointer over the plug-in, and choose |image1| > **Version**. On the page that is displayed, check the plug-in status.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                   |
      |                                   | -  **Unreleased**: When you create a plug-in or create a plug-in version, the plug-in status is **Unreleased**. You can click the version number to edit the plug-in.                                                                                             |
      |                                   | -  **Released**: After you click **Release** in the **Operation** column, the plug-in status changes to **Released**. You can click the version number to view the plug-in details.                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Creating a version                | Locate the target plug-in, hover the mouse pointer over the plug-in, and choose |image2| > **Version**. Click **Create Version**. On the displayed page, set the plug-in information.                                                                             |
      |                                   |                                                                                                                                                                                                                                                                   |
      |                                   | Precautions:                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                   |
      |                                   | -  A maximum of five versions can be created for a plug-in.                                                                                                                                                                                                       |
      |                                   | -  If there is only one plug-in version, only **Copy** is available in the **Operation** column. If there is more than one plug-in, both **Copy** and **Delete** are available in the **Operation** column. You can click **Delete** to delete a plug-in version. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Modifying a plug-in               | Locate the target plug-in, hover the mouse pointer over the plug-in, and choose |image3| > **Modify**. On the displayed page, modify the plug-in information.                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a plug-in                | Locate the target plug-in, hover the mouse pointer over the plug-in, and choose |image4| > **Delete**. On the displayed page, click **Yes** to delete the plug-in.                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                   |
      |                                   | If a collection task has been configured for a plug-in, deleting the plug-in will also delete the collection task.                                                                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _agent_01_00272__agent_01_0027_section59610573377:


Connecting Custom Plug-ins to AOM
---------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center** to go to the old access center. (The new access center does not support the connection of custom plug-ins. To switch from the new access center to the old one, click **Back to Old Version** in the upper right corner.)

#. In the **Custom Prometheus Plug-in Access** panel, click the created custom plug-in.

#. .. _agent_01_00272__agent_01_0027_li2966194183215:

   On the displayed page, set parameters by referring to the following table.

   .. table:: **Table 4** Parameters for configuring a collection task

      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation             | Parameter                     | Description                                                                                                                                                                                                                     |
      +=======================+===============================+=================================================================================================================================================================================================================================+
      | Select Instance       | Prometheus Instance           | Select a Prometheus instance for ECS to store collected data.                                                                                                                                                                   |
      |                       |                               |                                                                                                                                                                                                                                 |
      |                       |                               | A collection task is associated with the Prometheus instance to mark and classify collected data. If no Prometheus instance is available, :ref:`create one <mon_01_0072>`.                                                      |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Set Plug-in           | OS                            | Operating system of the host. Options: **Linux** and **Windows**. For a custom plug-in, the OS is automatically selected.                                                                                                       |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Collection Plug-in            | (Default) Created custom plug-in.                                                                                                                                                                                               |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Plug-in Version               | Select a plug-in version. Plug-in versions that have not been released are dimmed and cannot be selected.                                                                                                                       |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Set Collection Task   | Collection Task Name          | Name of a collection task. Enter 1 to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                                 |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Host                          | Click **Add Host**. On the **Add Host** page, select the host for configuring the collection task and installing Exporter.                                                                                                      |
      |                       |                               |                                                                                                                                                                                                                                 |
      |                       |                               | -  Search for and select a host by the host name, IP address, or Agent status.                                                                                                                                                  |
      |                       |                               | -  You can click |image5| in the upper right corner to deselect the selected host.                                                                                                                                              |
      |                       |                               | -  Ensure that the UniAgent of the selected host is running. Otherwise, no data can be collected.                                                                                                                               |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Plug-in Collection Parameters | Set parameters for the custom plug-in script. They come from the default script parameters you define when :ref:`creating a custom plug-in script <agent_01_00272__agent_01_0027_en-us_topic_0000001875791466_li164767163242>`. |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Advanced Settings             | Configure the following parameters:                                                                                                                                                                                             |
      |                       |                               |                                                                                                                                                                                                                                 |
      |                       |                               | -  **Collection Period (s)**: O&M data collection period, in seconds. Options: **10s**, **30s**, and **60s** (default).                                                                                                         |
      |                       |                               | -  **Timeout Period (s)**: the maximum time allowed for executing a collection task, in seconds. Options: **10s**, **30s**, and **60s** (default). The timeout period cannot exceed the collection period.                      |
      |                       |                               | -  **Executor**: user who executes the collection task, that is, the user of the selected host. Default: **root**. Enter a username. Recommended: **root**.                                                                     |
      +-----------------------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.

#. The connected plug-in will be displayed on the **Collection Tasks** tab page of the plug-in card. Click the plug-in card. On the **Collection Tasks** tab page, click the target collection task to view its details.

   You can also perform the operations listed in the following table on the collection task.

   .. table:: **Table 5** Related operations

      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                              | Description                                                                                                                                   |
      +========================================+===============================================================================================================================================+
      | Checking a collection task             | Click a collection task to go to its details page.                                                                                            |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Starting or stopping a collection task | Click the button in the **Start/Stop** column of a collection task to start or stop it.                                                       |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Searching for a collection task        | Set filter criteria or enter keywords to search for a collection task.                                                                        |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Changing target hosts                  | Click |image6| in the **Operation** column of the target collection task. On the displayed page, change target hosts.                         |
      |                                        |                                                                                                                                               |
      |                                        | You can only change the target hosts for the collection tasks created using custom plug-ins.                                                  |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Sorting collection tasks               | Click |image7| in the **Timeout Period** or **Collection Period** column to sort collection tasks.                                            |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Copying a collection task              | Click |image8| in the **Operation** column of a collection task. On the displayed page, modify parameters as required.                        |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Modifying a collection task            | Choose |image9| > **Modify** in the **Operation** column of the target collection task. On the displayed page, modify parameters as required. |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a collection task             | Locate a collection task and choose |image10| > **Delete** in the **Operation** column. On the displayed page, confirm the deletion.          |
      +----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002370949493.png
.. |image2| image:: /_static/images/en-us_image_0000002336871520.png
.. |image3| image:: /_static/images/en-us_image_0000002337031280.png
.. |image4| image:: /_static/images/en-us_image_0000002370949497.png
.. |image5| image:: /_static/images/en-us_image_0000002371029153.png
.. |image6| image:: /_static/images/en-us_image_0000002371029133.png
.. |image7| image:: /_static/images/en-us_image_0000002337030800.png
.. |image8| image:: /_static/images/en-us_image_0000002337030820.png
.. |image9| image:: /_static/images/en-us_image_0000002371029145.png
.. |image10| image:: /_static/images/en-us_image_0000002371029157.png
