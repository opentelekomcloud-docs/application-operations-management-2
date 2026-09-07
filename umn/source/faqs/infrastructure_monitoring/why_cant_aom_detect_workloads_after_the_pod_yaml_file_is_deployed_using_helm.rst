:original_name: aom_06_0041.html

.. _aom_06_0041:

Why Can't AOM Detect Workloads After the Pod YAML File Is Deployed Using Helm?
==============================================================================

Symptom
-------

After a pod is deployed using Helm, AOM cannot find the corresponding workload.

Possible Cause
--------------

On the workload page of the CCE console, find the record of the pod deployed using Helm, and compare its YAML file with the YAML file of the pod directly deployed on the CCE console. It is found that the YAML file of the pod deployed using Helm does not contain required environment parameters.


.. figure:: /_static/images/en-us_image_0000002371028837.png
   :alt: **Figure 1** Comparing YAML files

   **Figure 1** Comparing YAML files

Solution 1
----------

#. Log in to the CCE console and click a target cluster.

#. Choose **Workloads** in the navigation pane, and select the workload (pod deployed using Helm) whose metrics have not been reported to AOM.

#. Choose **More** > **Edit YAML** in the **Operation** column where the target workload is located.

#. In the displayed dialog box, locate **spec.template.spec.containers**.

#. Add environment parameters to the end of the **image** field, as shown in :ref:`Figure 2 <aom_06_0041__fig1263315325201>`.

   .. code-block::

      env:
           - name: PAAS_APP_NAME
             value: XXXXXXXXXXXX
           - name: PAAS_NAMESPACE
             value: XXXXXXXXXX
           - name: PAAS_PROJECT_ID
             value: 2a***********************cf

   -  **PAAS_APP_NAME**: application name, that is, the name of the workload to be deployed.

   -  **PAAS_NAMESPACE**: namespace of the CCE cluster where the workload to be deployed is located. To obtain the namespace, go to the namespace page on the CCE cluster details page.

   -  **PAAS_PROJECT_ID**: project ID of the tenant.

      Replace the values of the preceding environment parameters based on site requirements.

   .. _aom_06_0041__fig1263315325201:

   .. figure:: /_static/images/en-us_image_0000002370948689.png
      :alt: **Figure 2** Adding environment parameters

      **Figure 2** Adding environment parameters

#. Click **Confirm**.

Solution 2
----------

Add the following environment parameters to the YAML file for deploying the pod using Helm and then deploy the pod again.

.. code-block::

   env:
        - name: PAAS_APP_NAME
          value: XXXXXXXXXXXX
        - name: PAAS_NAMESPACE
          value: XXXXXXXXXX
        - name: PAAS_PROJECT_ID
          value: 2a***********************cf

-  **PAAS_APP_NAME**: application name, that is, the name of the workload to be deployed.

-  **PAAS_NAMESPACE**: namespace of the CCE cluster where the workload to be deployed is located. To obtain the namespace, go to the namespace page on the CCE cluster details page.

-  **PAAS_PROJECT_ID**: project ID of the tenant.

   Replace the values of the preceding environment parameters based on site requirements.


.. figure:: /_static/images/en-us_image_0000002370948689.png
   :alt: **Figure 3** Adding environment parameters

   **Figure 3** Adding environment parameters
