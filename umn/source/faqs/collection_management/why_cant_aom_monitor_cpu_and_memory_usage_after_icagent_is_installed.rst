:original_name: aom_06_0047.html

.. _aom_06_0047:

Why Can't AOM Monitor CPU and Memory Usage After ICAgent Is Installed?
======================================================================

Symptom
-------

AOM cannot monitor information (such as CPU and memory usage) after the ICAgent is installed.

Possible Cause
--------------

-  Port 8149 is not connected.
-  The node time on the user side is inconsistent with the time of the current time zone.

Solution
--------

#. Log in to the server where the ICAgent is installed as the **root** user.

#. Check whether the ICAgent can report metrics:

   .. code-block::

      cat /var/ICAgent/oss.icAgent.trace | grep httpsend | grep MONITOR

   -  If the command output contains **failed**, the ICAgent cannot report metrics. In this case, go to :ref:`3 <aom_06_0047__en-us_topic_0000001411569738_li77391656131917>`.
   -  If the command output does not contain **failed**, the ICAgent can report metrics. In this case, go to :ref:`4 <aom_06_0047__en-us_topic_0000001411569738_li6100114191417>`.

#. .. _aom_06_0047__en-us_topic_0000001411569738_li77391656131917:

   Check whether the port is connected.

   a. Obtain the access IP address:

      .. code-block::

         cat /opt/oss/servicemgr/ICAgent/envs/ICProbeAgent.properties | grep ACCESS_IP

   b. Check the connectivity of port 8149:

      .. code-block::

         curl -k https://ACCESS_IP:8149

      -  If **404** is returned, the port is connected. In this case, contact technical support.
      -  If **404** is not returned, the port is not connected. In this case, contact the network administrator to open the port and reinstall the ICAgent. If the installation still fails, contact technical support.

#. .. _aom_06_0047__en-us_topic_0000001411569738_li6100114191417:

   Check the node time on the user side:

   .. code-block::

      date

   -  If the queried time is the same as the time of the current time zone, contact technical support.
   -  If they are different, go to :ref:`5 <aom_06_0047__en-us_topic_0000001411569738_li089634131819>`.

#. .. _aom_06_0047__en-us_topic_0000001411569738_li089634131819:

   Reconfigure the node time on the user side:

   .. code-block::

      date -s Time of the current time zone (for example, 12:34:56)
