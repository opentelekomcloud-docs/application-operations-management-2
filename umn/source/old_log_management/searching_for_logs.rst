:original_name: mon_01_0106.html

.. _mon_01_0106:

Searching for Logs
==================

AOM enables you to quickly query logs, and locate faults based on log sources and contexts.

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Log Management** > **Log Management**. On the displayed page, click **Old Edition** in the upper right corner.

#. On the **Log Search** page, click the **Component**, **System**, or **Host** tab and set filter criteria as prompted.

   -  You can search for logs by component, system, or host.

      -  For component logs, you can set filter criteria such as **Cluster**, **Namespace**, and **Component**. You can also click **Advanced Search** and set filter criteria such as **Instance**, **Host**, and **File**, and choose whether to enable **Hide System Component**.
      -  For system logs, you can set filter criteria such as **Cluster** and **Host**.
      -  For host logs, you can set filter criteria such as **Cluster** and **Host**.

   -  Enter a keyword in the search box. Rules are as follows:

      -  Enter keywords for exact search. A keyword is the word between two adjacent delimiters.
      -  Use an asterisk (*) or question mark (?) for fuzzy search, for example, **ER?OR**, **ROR\***, or **ER*R**.
      -  Enter a phrase for exact search. For example, enter **Start to refresh** or **Start-to-refresh**. Note that hyphens (-) are delimiters.
      -  Enter a keyword containing AND (&&) or OR (||) for search. For example, enter **query logs&&error\*** or **query logs||error**.
      -  If no log is returned, narrow down the search range, or add an asterisk (*) to the end of a keyword for fuzzy match.

#. .. _mon_01_0106__li34212241:

   View the search result of logs.

   The search results are sorted based on the log collection time, and keywords in them are highlighted. You can click |image1| in the **Time** column to switch the sorting order. |image2| indicates the default order. |image3| indicates the ascending order by time (the latest log is displayed at the bottom). |image4| indicates the descending order by time (the latest log is displayed at the top).

   a. AOM allows you to view context. Click **Context** in the **Operation** column to view the previous or next logs of a log for fault locating.

      **To ensure normal host and component running, some components (for example, kube-dns) provided by the system will run on the hosts. The logs of these components will also be queried during tenant log query.**

      -  In the **Display Rows** drop-down list, set the number of rows that display raw context data of the log.

         For example, select **200** from the **Display Rows** drop-down list.

         -  If there are 100 logs or more printed before a log and 99 or more logs printed following the log, the preceding 100 logs and following 99 logs are displayed as the context.
         -  If there are fewer than 100 logs (for example, 90) printed before a log and fewer than 99 logs (for example, 80) printed following the log, the preceding 90 logs and following 80 logs are displayed as the context.

      -  Click **Export Current Page** to export displayed raw context data of the log to a local PC.

   b. Click **View Details** on the left of the log list to view details such as host IP address and source.

#. (Optional) Click |image5| on the right of the **Log Search** page, select an export format, and export the search result to a local PC.

   Logs are sorted according to the order set in :ref:`4 <mon_01_0106__li34212241>` and a maximum of 5000 logs can be exported. For example, when 6000 logs in the search result are sorted in descending order, only the first 5000 logs can be exported.

   Logs can be exported in CSV or TXT format. You can select a format as required. If you select the CSV format, detailed information (such as the log content, host IP address, and source) can be exported. Only log content will be exported when you select the TXT format. Each line indicates a log.

#. (Optional) Click **Configure Dumps** to dump the searched logs to the same log file in the OBS bucket at a time. For details, see :ref:`Adding One-Off Dumps <mon_01_0109__en-us_topic_0169698290_section1130151415546>`.

.. |image1| image:: /_static/images/en-us_image_0000002337031496.png
.. |image2| image:: /_static/images/en-us_image_0000002337031488.png
.. |image3| image:: /_static/images/en-us_image_0000002370949701.png
.. |image4| image:: /_static/images/en-us_image_0000002371029853.png
.. |image5| image:: /_static/images/en-us_image_0000002336871740.png
