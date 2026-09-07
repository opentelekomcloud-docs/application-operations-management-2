:original_name: mon_01_0085.html

.. _mon_01_0085:

Using AOM to Monitor Application Processes
==========================================

An application groups identical or similar components based on service requirements. Applications are classified into system applications and custom applications. System applications are discovered based on built-in discovery rules, and custom applications are discovered based on custom rules. The application list displays the name, running status, and deployment mode of each application. AOM supports drill-down from applications to components, instances, and processes. By viewing the status of each layer, you can implement dimensional monitoring for applications. After application discovery rules are set, AOM automatically discovers applications that meet the rules and monitors related metrics. For details, see :ref:`Configuring AOM Application Discovery Rules <mon_01_0087>`.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Infrastructure Monitoring** > **Process Monitoring**. On the **Application Monitoring** tab page, check the application list.

   -  Set filter criteria in the search box to filter applications.
   -  Click |image1| in the upper right corner of the page and select or deselect the columns to display.

#. Click |image2| in the upper right corner of the page and select a desired value from the drop-down list.

   a. Set a time range to view applications. There are two methods to set a time range:

      Method 1: Use a predefined time label, such as **Last 30 minutes** or **Last hour** in the upper right corner of the page. You can select a time range as required.

      Method 2: Specify the start time and end time to customize a time range. You can specify 30 days at most.

   b. Set the interval for refreshing information. Click |image3| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.

#. Click an application name. On the page that is displayed, you can view the component list, host list, monitoring views, and alarms of the current application.

   -  On the **Component List** tab page, you can view the running status and resource usage of components. Click a component name to view the instances of the component. Click an instance name to view the monitoring view and alarm information.
   -  On the **Host List** tab page, you can view the running status and resource usage of hosts.
   -  On the **Monitoring Views** tab page, select a desired Prometheus instance to view the resource usage of the application. Click |image4| in the upper right corner of the page to view resource information in full screen.
   -  On the **Alarms** tab page, view the alarm details of the application. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.

.. |image1| image:: /_static/images/en-us_image_0000002337031432.png
.. |image2| image:: /_static/images/en-us_image_0000002337031420.png
.. |image3| image:: /_static/images/en-us_image_0000002371029789.png
.. |image4| image:: /_static/images/en-us_image_0000002337031428.png
