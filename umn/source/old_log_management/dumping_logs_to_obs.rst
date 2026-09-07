:original_name: mon_01_0109.html

.. _mon_01_0109:

Dumping Logs to OBS
===================

AOM enables you to dump logs to Object Storage Service (OBS) buckets for long-term storage. To store logs for a longer time, add log dumps.

AOM offers both periodic and one-off dump modes. You can choose one of them as required.

-  **Periodic dump**: Current logs are dumped in real time into an OBS bucket and 1-day logs are divided based on the dump cycle.

   To periodically store logs for a long period, add periodic dumps. For details, see :ref:`Adding Periodical Dumps <mon_01_0109__en-us_topic_0169698290_section246131702711>`.

-  **One-off dump**: Dump historical logs to a log file of an OBS bucket at one time.

   One-off dump is similar to the export function on the **Log Search** page. You can export up to 5000 logs on that page. When you need to export more logs but the export function cannot meet your needs, dump the logs at a time according to :ref:`Adding One-Off Dumps <mon_01_0109__en-us_topic_0169698290_section1130151415546>`.

Constraints
-----------

-  To add a log dump task, you must have OBS administrator permissions in addition to AOM and LTS permissions.
-  If you need to dump logs to OBS buckets in real time for long-term storage, use the log dump function of LTS.
-  Periodical dump is a near-real-time dump but has latency in minutes. The latency varies depending on the number of logs and log size. Details are as follows:

   -  If the number of logs generated within 5 minutes exceeds 1000 or the log size exceeds 2 MB, the logs are dumped in real time.
   -  If the number of logs generated within 5 minutes is less than 1000 or the log size is less than 2 MB, the logs are dumped every 5 minutes.

.. _mon_01_0109__en-us_topic_0169698290_section246131702711:

Adding Periodical Dumps
-----------------------

Assume that you need to dump the logs of the **als0320a** component into files in the **/home/Periodical Dump** directory of the **obs-store-test** OBS bucket in real time, and the dump cycle is 3 hours, perform the following steps:

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Log Management** > **Log Management**. On the displayed page, click **Old Edition** in the upper right corner.

#. On the **Log Transfer** tab page, click **Add Log Dump** in the upper right corner of the page. Then, set parameters according to :ref:`Table 1 <mon_01_0109__en-us_topic_0169698290_table1517618282520>` and click **OK**.

   .. _mon_01_0109__en-us_topic_0169698290_table1517618282520:

   .. table:: **Table 1** Periodical dump parameters

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                        | Example                                                                  |
      +=======================+====================================================================================================================================================================================================================================================================================================================================================================================================================================+==========================================================================+
      | Dump Mode             | Select **Periodic dump**.                                                                                                                                                                                                                                                                                                                                                                                                          | Periodic dump                                                            |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Filter Criteria       | Logs can be filtered by multiple criteria such as log type, cluster, or namespace, so that you can dump the logs that meet specific criteria.                                                                                                                                                                                                                                                                                      | Select the **Component** log type and select the **als0320a** component. |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Log Group             | Logs can be categorized into logical groups, so that you can dump them based on groups.                                                                                                                                                                                                                                                                                                                                            | log-group1                                                               |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Dump Cycle            | You can divide 1-day logs based on the dump cycle. There are "N" time segments in a day (Number of time segments = 24 hours/Dump cycle). The logs of the same time segment are dumped into the same log file.                                                                                                                                                                                                                      | 3 hours                                                                  |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                          |
      |                       | For example, if the dump cycle is set to 3 hours, there are 8 time segments in a day. The logs generated at 00:00-03:00 in a day are dumped to the log file in the **Log collection date** (format: **YYYY-MM-DD**) > **00** path, and the logs generated at 03:00-06:00 in a day are dumped to the log file in the **Log collection date** (format: **YYYY-MM-DD**) > **03** path. Other time segments can be deduced by analogy. |                                                                          |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Target OBS Bucket     | OBS bucket for storing logs. To create an OBS bucket, click **View OBS** to go to the OBS console.                                                                                                                                                                                                                                                                                                                                 | obs-store-test                                                           |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | OBS Bucket Directory  | OBS bucket directory for storing logs.                                                                                                                                                                                                                                                                                                                                                                                             | /home/Periodical Dump                                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+

   After the periodical dump is added, the new logs of the specified resource will be dumped into the OBS bucket in real time.

   In the preceding example, the logs of **als0320a** will be dumped into log files in the **/home/Periodical Dump** directory of the **obs-store-test** OBS bucket in real time, and the dump cycle is 3 hours.

#. Download the log files in the OBS bucket to a local host for locating faults.

   a. In the periodical dump list, click the target OBS bucket to go to the **Objects** page on the OBS console.

   b. On the **Objects** tab page, find the log files stored in OBS, such as **192.168.0.74_var-paas-sys-log-apm-count_warn.log** and **192.168.0.74_var-paas-sys-log-apm-debug_erro.trace**.

      **Paths of the log files dumped to the OBS bucket**: Log file paths are related to the selected log types, as shown in the following table.

      .. table:: **Table 2** Paths of the log files dumped to the OBS bucket

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Log Type                          | Log File Path                                                                                                                                                              |
         +===================================+============================================================================================================================================================================+
         | Component                         | **Bucket directory** > **Log group name** > **Cluster name** > **Component name** > **Log collection date** (format: **YYYY-MM-DD**) > **File ID** (format: **0X**)        |
         |                                   |                                                                                                                                                                            |
         |                                   | For example, **obs-store-test** > **home** > **Periodical Dump** > **log-group1** > **zhqtest0112n** > **als0320a** > **2019-03-22** > **03**.                             |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Host                              | **Belong bucket directory** > **Log group name** > **CONFIG_FILE** > **default_appname** > **Log collection date** (format: **YYYY-MM-DD**) > **File ID** (format: **0X**) |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | OS                                | **Belong bucket directory** > **Log group name** > **Cluster name** > **Log collection date** (format: **YYYY-MM-DD**) > **File ID** (format: **0X**)                      |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      **Names of the log files dumped to the OBS bucket**: **Host IPv4 address_Log file source_Log file name**. Note that slashes (/) in a log file source must be replaced with hyphens (-). For example, **192.168.0.74_var-paas-sys-log-apm-count_warn.log** or **192.168.0.74_var-paas-sys-log-apm-debug_erro.trace**.

   c. Select the required log file and click **Download** to download it to the default download path. To save the log file to a custom path, choose **More** > **Download As**.

.. _mon_01_0109__en-us_topic_0169698290_section1130151415546:

Adding One-Off Dumps
--------------------

For example, to dump the logs that contain the **warn** keyword in the last 30 minutes of **als0320a** to the **/home/One-off Dump** directory of the **obs-store-test** OBS bucket, perform the following steps:

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Log Management** > **Log Management**. On the displayed page, click **Old Edition** in the upper right corner.

#. On the **Log Transfer** tab page, click **Add Log Dump** in the upper right corner of the page. Then, set parameters according to :ref:`Table 3 <mon_01_0109__en-us_topic_0169698290_table93147547513>` and click **OK**.

   .. _mon_01_0109__en-us_topic_0169698290_table93147547513:

   .. table:: **Table 3** One-off dump parameters

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                         | Example                                                                                                                 |
      +=======================+=====================================================================================================================================================================+=========================================================================================================================+
      | Dump Mode             | Select **One-off dump**.                                                                                                                                            | One-off dump                                                                                                            |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Filter Criteria       | Logs can be filtered by multiple criteria such as log collection time, cluster, or namespace, so that you can dump the logs that meet specific criteria.            | Set the log collection time to **Last 30 minutes**, select the **als0320a** component, and set the keyword to **warn**. |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Log Group             | Logs can be categorized into logical groups, so that you can dump them based on groups. **After a dump task is deleted, log groups will also be deleted.**          | log-group2                                                                                                              |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Target OBS Bucket     | OBS bucket for storing logs.                                                                                                                                        | obs-store-test                                                                                                          |
      |                       |                                                                                                                                                                     |                                                                                                                         |
      |                       | -  If no OBS bucket is available, click **View OBS** to create a bucket on the OBS console.                                                                         |                                                                                                                         |
      |                       | -  If you select an unauthorized OBS bucket, AOM will take 15 minutes to authorize the ACL for the bucket. If your configuration fails, try again 15 minutes later. |                                                                                                                         |
      |                       | -  Data cannot be dumped to an OBS bucket whose storage class is **Archive** or for which cross-region replication has been configured.                             |                                                                                                                         |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | OBS Bucket Directory  | OBS bucket directory for storing logs. **If this parameter is left blank, logs are stored in the** **root** **directory of the OBS bucket by default.**             | /home/One-off Dump                                                                                                      |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

   After the one-off dump is added and the dump status changes to **Dumped**, the historical logs that meet criteria are dumped into the same log file of the OBS bucket at one time.

   For example, the historical logs that contain the **warn** keyword in the last 30 minutes of **als0320a** will be dumped to the **log-group2_shard_0(custom).log** file in the **/home/One-off Dump** directory of the **obs-store-test** OBS bucket at one time.

#. Download the log files in the OBS bucket to a local host for locating faults.

   a. In the one-off dump list, click the target OBS bucket to go to the **Objects** page on the OBS console.

   b. On the **Objects** tab page, find the log file stored in OBS, for example, **/home/One-off Dump/log-group2_shard_0(custom).log**.

      **Paths of the log files dumped to the OBS bucket**: **OBS bucket** > **Belong bucket directory** For example, **obs-store-test/home/One-off Dump**.

      **Names of the log files dumped to the OBS bucket**: Log file names are related to dump file formats, as shown in the following table.

      .. table:: **Table 4** Names of the log files dumped to the OBS bucket

         +------------------------------------------------------------------------------------+
         | Log File Name                                                                      |
         +====================================================================================+
         | -  Log group name_shard_0(custom), for example, **log-group2_shard_0(custom).log** |
         | -  Log group name_shard_1(custom)                                                  |
         +------------------------------------------------------------------------------------+

   c. Select the required log file and click **Download** to download it to the default download path. To save the log file to a custom path, choose **More** > **Download As**.
