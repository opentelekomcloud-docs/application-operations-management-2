:original_name: mon_01_0007.html

.. _mon_01_0007:

AOM Alarm Rule Overview
=======================

AOM allows you to set alarm and event rules. You can create metric/log alarm rules to monitor the real-time usage of resources such as hosts and components in the environment, helping you quickly detect, locate, and rectify faults. By creating event alarm rules, you can simplify alarm notifications and quickly troubleshoot resource usage problems.

Description
-----------

-  :ref:`Creating an AOM Metric Alarm Rule <mon_01_0008>`

   For metric alarm rules, you can set threshold conditions for resource metrics. If a metric value meets a threshold condition, AOM generates a threshold alarm. If no metric data is reported, AOM generates an insufficient data event.

-  :ref:`Creating an AOM Event Alarm Rule <mon_01_0010>`

   You can set event conditions for services by setting event alarm rules. When the resource data meets an event condition, an event alarm is generated.

-  :ref:`Creating an AOM Log Alarm Rule <mon_01_0127>`

   You can create alarm rules based on keyword statistics so that AOM can monitor log data in real time and report alarms if there are any.

-  :ref:`Creating AOM Alarm Rules in Batches <mon_01_0075>`

   An alarm template is a combination of alarm rules based on cloud services. You can use an alarm template to create threshold alarm rules, event alarm rules, or PromQL alarm rules for multiple metrics of one cloud service in batches.

Constraints
-----------

A maximum of 3,000 metric/event alarm rules can be created. If the number of alarm rules has reached the upper limit, delete unnecessary rules and create new ones.
