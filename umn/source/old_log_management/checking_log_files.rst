:original_name: mon_01_0107.html

.. _mon_01_0107:

Checking Log Files
==================

You can quickly check log files of component instances or hosts to locate faults.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Log Management** > **Log Management**. On the displayed page, click **Old Edition** in the upper right corner.

#. On the page that is displayed, click the **Component** or **Host** tab and click a name. Information such as the log file name and latest written time is displayed on the right of the page.

#. Click **View** in the **Operation** column of the desired instance. :ref:`Table 1 <mon_01_0107__table186411152115819>` shows how to view log file details.

   .. _mon_01_0107__table186411152115819:

   .. table:: **Table 1** Operations

      +-----------------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation             | Settings                  | Description                                                                                                                                                                                                                                                                          |
      +=======================+===========================+======================================================================================================================================================================================================================================================================================+
      | Setting a time range  | Date                      | Click |image1| to select a date.                                                                                                                                                                                                                                                     |
      +-----------------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Viewing log files     | Clear                     | Click **Clear** to clear the logs displayed on the screen. Logs displayed on the screen will be cleared, but will not be deleted.                                                                                                                                                    |
      +-----------------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Viewing logs in real time | Real-time viewing is disabled by default. You can click **Enable Real-Time Viewing** as required. After this function is enabled, the latest written logs can be viewed. Logs can be searched only when real-time viewing is disabled.                                               |
      |                       |                           |                                                                                                                                                                                                                                                                                      |
      |                       |                           | For real-time log viewing, AOM automatically highlights exception keywords in logs, facilitating fault locating. Such keywords are case-sensitive. For example, when you enter **format** to search, **format** in logs will be highlighted, but **Format** and **FORMAT** will not. |
      +-----------------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) Click **Configure Dumps** in the **Operation** column of the target instance to dump its logs to the same log file in the OBS bucket at a time. For details, see :ref:`Adding One-Off Dumps <mon_01_0109__en-us_topic_0169698290_section1130151415546>`.

.. |image1| image:: /_static/images/en-us_image_0000002336872144.png
