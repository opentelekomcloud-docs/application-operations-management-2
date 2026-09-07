:original_name: mon_01_0038.html

.. _mon_01_0038:

Using AOM to Monitor Hosts
==========================

Hosts include the Elastic Cloud Server (ECS) and Bare Metal Server (BMS). AOM can monitor the hosts created during CCE cluster creation and those created in non-CCE environments. In addition, hosts support IPv4 addresses.

Host monitoring displays resource usage, trends, and alarms, so that you can quickly respond to malfunctioning hosts and handle errors to ensure smooth host running.

Constraints
-----------

-  A maximum of five tags can be added to a host, and each tag must be unique.
-  The same tag can be added to different hosts.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Infrastructure Monitoring** > **Host Monitoring**.

   -  Set filter criteria (such as the running status, host type, host name, and IP address) above the host list.
   -  You can enable or disable **Hide master host**. By default, this option is enabled.
   -  Click |image1| next to **Hide master host** to synchronize host information.
   -  In the upper right corner of the page, set filter criteria.

      -  Set a time range to check the hosts reported. You can use a predefined time label, such as **Last hour** and **Last 6 hours**, or customize a time range. Max.: 30 days.
      -  Set the interval for refreshing information. Click |image2| and select a value from the drop-down list as required, such as **Refresh manually**, **30 seconds auto refresh**, **1 minute auto refresh**, or **5 minutes auto refresh**.
      -  Click |image3| in the upper right corner and select or deselect **Tags**.

3. Perform the following operations if needed:

   -  **Adding an alias**

      If a host name is too complex to identify, you can add an alias, which makes it easy to identify a host as required.

      In the host list, click |image4| in the **Operation** column of the target host, enter an alias, and click **OK**. The added alias can be modified but cannot be deleted.

   -  **Adding a tag**

      Tags are identifiers of hosts. You can manage hosts using tags. After a tag is added, you can quickly identify and select a host.

      In the host list, click |image5| in the **Operation** column of the target host. In the displayed dialog box, enter a tag key and value, and click |image6| and **OK**.

   -  **Synchronizing host data**

      In the host list, locate the target host and click |image7| in the **Operation** column to synchronize host information.

4. Set filter criteria to search for the desired host. **Hosts cannot be searched by alias.**
5. Click a host name. On the displayed host details page, you can view the running status and ID of the host.
6. Click any tab. In the list, you can monitor the instance resource usage and health status, and information about common resources such as GPUs and NICs.

   -  On the **Process List** tab page of the ECS host, you can view the process status and IP address of the host.

      -  In the search box in the upper right corner of the process list, you can set search criteria such as the process name to filter processes.
      -  Click |image8| in the upper right corner to obtain the latest process information within the specified time range.

   -  On the **Pods** tab page of the CCE host, you can view the pod status and node IP address.

      -  Click a pod name to view details about the container and process of the pod.
      -  In the search box in the upper right corner of the pod list, you can set search criteria such as pod names to filter pods.
      -  Click |image9| in the upper right corner to obtain the latest pod information within the specified time range.

   -  On the **Monitoring Views** tab page, view key metric graphs of the host.
   -  On the **File Systems** tab page, view the basic information about the file system of the host. Click a disk file partition to monitor its metrics on the **Monitoring Views** page.
   -  On the **Disks** tab page, view the basic information about the disks of the host. Click a disk to monitor its metrics on the **Monitoring Views** page.
   -  On the **Disk Partitions** tab page, view the disk partition information about the host. Click a disk partition to monitor its metrics on the **Monitoring Views** page.
   -  Click the **NICs** tab to view the basic information about the NICs of the host. Click a NIC to monitor its metrics on the **Monitoring Views** page.
   -  Click the **GPUs** tab to view the basic information about the GPUs of the host. Click a GPU to monitor its metrics on the **Monitoring Views** page.
   -  On the **Events** tab page, view the event details of the host. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
   -  On the **Alarms** tab page, view the alarm details of the host. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
   -  On the **File Systems**, **Disks**, **Disk Partitions**, **NICs**, or **GPUs** tab page, click |image10| in the upper right corner of the resource list and select or deselect items to display. **Disk partitions are supported by CentOS 7.x and EulerOS 2.5.**

.. |image1| image:: /_static/images/en-us_image_0000002336871696.png
.. |image2| image:: /_static/images/en-us_image_0000002336871704.png
.. |image3| image:: /_static/images/en-us_image_0000002337031452.png
.. |image4| image:: /_static/images/en-us_image_0000002371029821.png
.. |image5| image:: /_static/images/en-us_image_0000002370949657.png
.. |image6| image:: /_static/images/en-us_image_0000002370949645.png
.. |image7| image:: /_static/images/en-us_image_0000002336871692.png
.. |image8| image:: /_static/images/en-us_image_0000002336871700.png
.. |image9| image:: /_static/images/en-us_image_0000002370949649.png
.. |image10| image:: /_static/images/en-us_image_0000002370949653.png
