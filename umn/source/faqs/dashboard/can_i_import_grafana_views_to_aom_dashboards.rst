:original_name: aom_06_0048.html

.. _aom_06_0048:

Can I Import Grafana Views to AOM Dashboards?
=============================================

Symptom
-------

Can I import Grafana views to AOM dashboards?

Solution
--------

Obtain the Prometheus statement of a Grafana view and then create a graph in AOM by using the Prometheus statement.

Procedure:

#. .. _aom_06_0048__li11671146165216:

   Log in to Grafana and obtain the Prometheus statement of a Grafana view.

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Metric Browsing**.

#. Select a target Prometheus instance from the drop-down list.

#. Click **Prometheus statement** and enter the Prometheus statement obtained in :ref:`1 <aom_06_0048__li11671146165216>`.

#. Select a metric and click |image1| in the upper right corner of the metric list.

#. In the **Add to Dashboard** dialog box, select a dashboard, set a graph name, and click **Confirm**.

   Then you can view the Grafana view in AOM.

.. |image1| image:: /_static/images/en-us_image_0000002371028841.png
