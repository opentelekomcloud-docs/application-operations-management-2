:original_name: mon_01_0235.html

.. _mon_01_0235:

AOM Overview
============

The **Overview** page provides panoramic monitoring of resources and logs. It displays :ref:`Updates <mon_01_0235__section154711958205011>`, :ref:`Alarm Overview <mon_01_0235__section3981652132615>`, :ref:`Usage Overview <mon_01_0235__section1465244673412>`, :ref:`Prometheus Monitoring <mon_01_0235__section208932045115>`, :ref:`Log Monitoring <mon_01_0235__section363712291549>`, :ref:`Common Functions <mon_01_0235__section6621013511>`, and :ref:`FAQs <mon_01_0235__section158941446254>`.

Constraints
-----------

-  To view LTS data on the **Panorama** page, you need to obtain the **lts:trafficStatistic:get** and **lts:groups:list** permissions in advance.
-  AOM automatically checks ICAgent versions. If AOM detects that an ICAgent version is no longer maintained, a message indicating that the ICAgent version is too early will be displayed when you log in to the AOM console. You can authorize an automatic ICAgent upgrade during off-peak hours or :ref:`manually upgrade the ICAgent <agent_01_0028>` on the UniAgent management page. If you do not need to upgrade ICAgent, select **Do not show again**.

Viewing Overview
----------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Overview**.

#. Click the time selection box in the upper right corner of the page and select a period from the drop-down list. Options: **Last 30 minutes**, **Last hour**, **Last 6 hours**, **Last day**, and **Last week**.

   You can also perform the following operations if needed:

   -  Manual refresh: Click |image1| in the upper right corner of the page to manually refresh the page.
   -  Automatic refresh: Click the drop-down arrow next to |image2| in the upper right corner of the page and select an automatic refresh interval.

.. _mon_01_0235__section154711958205011:

Updates
-------

This card displays the latest functions of AOM 2.0.

.. _mon_01_0235__section3981652132615:

Alarm Overview
--------------

This card displays the total number of alarms, number of alarms of each severity, and alarm sources. You can click **alarm rules** to :ref:`configure alarm rules <mon_01_0006>`.

.. _mon_01_0235__section1465244673412:

Usage Overview
--------------

This card displays the number of resources under Prometheus and cloud log monitoring.

-  **Prometheus Monitoring**: displays the number of Prometheus instances. You can click **Ingest Metric** to go to the :ref:`instance list <mon_01_0072>` page.
-  **Cloud Log Monitoring**: displays the number of monitored log groups and log streams. You can click **Ingest Log** to go to the :ref:`Log Management <mon_01_0027>` page.

.. _mon_01_0235__section208932045115:

Prometheus Monitoring
---------------------

This card displays the Prometheus instances you have created. You can view the instance name, instance type, basic metrics, custom metrics, and billing mode of each instance. By default, the five Prometheus instances with the most basic metrics are displayed. You can also sort the instances by instance name, custom metrics, or billing mode.

-  **Usage Statistics**: Click **Usage Statistics** to go to the :ref:`Usage Statistics <mon_01_0125>` page.
-  **Create an instance**: Click **Create an Instance** to go to the :ref:`Instances <mon_01_0072>` page.
-  **Access Center**: Click **Access Center** to go to the :ref:`Access Center <mon_01_0196>` page.

.. _mon_01_0235__section363712291549:

Log Monitoring
--------------

This card displays the read/write traffic, index traffic-standard log stream graph, and top 5 log groups with the most log streams. By default, only the top 5 log groups with the most log streams are displayed. You can sort log groups by log group name, remark, log streams, or tags.

-  **Usage Statistics**: Click **Usage Statistics** to go to the :ref:`Log Management <mon_01_0027>` page.
-  **Add Log Group**: Click **Add Log Group** to go to the :ref:`Log Management <mon_01_0027>` page.
-  **Access Center**: Click **Access Center** to go to the :ref:`Access Center <mon_01_0196>` page.

.. _mon_01_0235__section6621013511:

Common Functions
----------------

This card displays common functions of AOM.

-  **Customize Alarm Template**: Click **Customize Alarm Template** to go to the :ref:`Alarm Templates <mon_01_0075>` page.
-  **Create Alarm Rule**: Click **Create Alarm Rule** to create :ref:`a metric alarm rule <mon_01_0008>` or :ref:`an event alarm rule <mon_01_0010>`.
-  **Create Notification Rule**: Click **Create Notification Rule** to go to the :ref:`Alarm Notifications <mon_01_0013>` page.
-  **Create Message Template**: Click **Create Message Template** to go to the :ref:`Message Templates <mon_01_0016>` page.
-  **Customize Dashboard**: Click **Customize Dashboard** to go to the :ref:`Dashboard <mon_01_0040>` page.

.. _mon_01_0235__section158941446254:

FAQs
----

This card displays the FAQs about AOM 2.0. For more details, see :ref:`FAQs <aom_06_0033>`.

.. |image1| image:: /_static/images/en-us_image_0000002370949937.png
.. |image2| image:: /_static/images/en-us_image_0000002337031744.png
