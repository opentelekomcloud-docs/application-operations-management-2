:original_name: mon_01_0011.html

.. _mon_01_0011:

Checking AOM Alarms or Events
=============================

The **Alarm List** page allows you to query and handle alarms and events, so that you can quickly detect, locate, and rectify faults.

Function Introduction
---------------------

-  The alarm list provides the following key functions:

   -  Alarm list: Check alarm information by alarm severity in a graph.
   -  Advanced filtering: Filter alarms by alarm severity, source, or keyword in the search box. By default, alarms are filtered by alarm severity.
   -  Alarm clearance: Clear alarms one by one or in batches.
   -  Alarm details: Check the alarm object and handling suggestions in the alarm details. Handling suggestions are provided for all alarms.

-  The event list provides the following key functions:

   -  Event list: Check event information by event severity in a graph.
   -  Advanced filtering: Filter events by event severity, source, or keyword in the search box. By default, events are filtered by event severity.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Alarm Center** > **Alarm List**.

#. Click the **Alarms** or **Events** tab to check alarms or events.

   a. Set a time range to check alarms or events. You can use a predefined time label, such as **Last hour** and **Last 6 hours**, or customize a time range. Max.: 31 days.
   b. Set the interval for refreshing alarms or events. Click |image1| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.
   c. Set filter criteria and click |image2| to check the alarms or events generated in the period. You can filter alarms or events through the search box.

      .. table:: **Table 1** Search criteria

         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
         | Search Criteria       | Description                                                                                                                                                            | Example                                                                                                                    |
         +=======================+========================================================================================================================================================================+============================================================================================================================+
         | Alarm/Event Severity  | Search by alarm/event severity. Options:                                                                                                                               | **Major**: Filter the alarms whose severity is **Major** within the specified time range.                                  |
         |                       |                                                                                                                                                                        |                                                                                                                            |
         |                       | -  Critical                                                                                                                                                            |                                                                                                                            |
         |                       | -  Major                                                                                                                                                               |                                                                                                                            |
         |                       | -  Minor                                                                                                                                                               |                                                                                                                            |
         |                       | -  Warning                                                                                                                                                             |                                                                                                                            |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
         | Resource Type         | Search by resource type.                                                                                                                                               | **Host**: Filter the alarms whose resource type is **Host** within the specified time range.                               |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
         | Alarm/Event Source    | You can select an alarm source to search for alarms or select an event source to search for events.                                                                    | **AOM**: Filter the alarms whose source is **AOM** within the specified time range.                                        |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
         | Alarm/Event Keyword   | -  **Alarm Keyword**: Fuzzy search by alarm name, alarm source, or resource type. Select **Alarm Keyword** in the search box and then enter a keyword.                 | **AOMRule**: Filter the alarm named **AOMRule** within the specified time range.                                           |
         |                       | -  **Event Keyword**: Fuzzy search by event name, event source, resource type, or other keywords. Select **Event Keyword** in the search box and then enter a keyword. |                                                                                                                            |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
         | Custom Attribute      | Exact query by custom attribute.                                                                                                                                       | -  **nodeIP=192.168.0.106**: Filter the alarms whose host IP address is **192.168.0.106** within the specified time range. |
         |                       |                                                                                                                                                                        |                                                                                                                            |
         |                       | Select **Custom Attribute** in the search box and then enter "custom attribute name=custom attribute value".                                                           |                                                                                                                            |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+

#. Perform the operations listed in :ref:`Table 2 <mon_01_0011__table48312734713>` as required:

   .. _mon_01_0011__table48312734713:

   .. table:: **Table 2** Operations

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================+
      | Checking alarm/event statistics   | Click |image3|, and check alarm/event statistics that meet filter criteria within a specific time range on a bar graph.                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Downloading alarms                | Click |image4| to download alarms. A maximum of 10,000 alarms can be downloaded each time.                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Clearing alarms                   | You can clear alarms after the problems that cause them are resolved.                                                                                                                       |
      |                                   |                                                                                                                                                                                             |
      |                                   | -  To clear an alarm, click |image5| in the **Operation** column of the target alarm.                                                                                                       |
      |                                   | -  To clear one or more alarms, select them and click **Clear** in the displayed dialog box.                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Viewing alarm details             | Click an alarm name to view alarm details, including alarm information and handling suggestions. You can also view a bound alarm notification rule or noise reduction rule if there is any. |
      |                                   |                                                                                                                                                                                             |
      |                                   | -  On the **Alarm Info** tab page, click the alarm rule in blue to drill down to check details.                                                                                             |
      |                                   | -  On the **Alarm Info** tab page, click a custom attribute and choose **Copy** or **Add to Search**.                                                                                       |
      |                                   |                                                                                                                                                                                             |
      |                                   |    -  **Copy**: Copy the custom attribute.                                                                                                                                                  |
      |                                   |    -  **Add to Search**: Filter alarms by custom attribute in the search box on the **Alarm List** page.                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Checking event details            | Click an event name to check event details and handling suggestions.                                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Checking cleared alarms           | Click **Active Alarms** in the upper right corner and select **Historical Alarms** from the drop-down list to check alarms that have been cleared.                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002336872192.png
.. |image2| image:: /_static/images/en-us_image_0000002337031936.png
.. |image3| image:: /_static/images/en-us_image_0000002370950145.png
.. |image4| image:: /_static/images/en-us_image_0000002370950129.png
.. |image5| image:: /_static/images/en-us_image_0000002371030293.png
