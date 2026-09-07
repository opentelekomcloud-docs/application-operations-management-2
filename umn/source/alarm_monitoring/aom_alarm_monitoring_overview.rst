:original_name: mon_01_0005.html

.. _mon_01_0005:

AOM Alarm Monitoring Overview
=============================

AOM provides alarm monitoring capabilities. Alarms are reported when AOM or an external service is abnormal or may cause exceptions. You need to take measures accordingly. Otherwise, service exceptions may occur. Events generally carry some important information. They are reported when AOM or an external service has some changes. Such changes do not necessarily cause service exceptions.

Description
-----------

-  Alarm notification: Create a notification rule and associate it with an SMN topic and a message template. If the log/resource/metric data meets the alarm condition, the system sends an alarm notification based on the associated SMN topic and message template.
-  Alarm noise reduction: The system processes alarms based on noise reduction rules to prevent an alarm storm.
-  Alarm rules: Create alarm or event rules to monitor resource usage in real time.
-  Viewing alarms or events: Query alarms and events for quick fault detection, locating, and recovery.
