:original_name: aom_06_0010.html

.. _aom_06_0010:

How Do I Create the apm_admin_trust Agency?
===========================================

Creating the apm_admin_trust Agency
-----------------------------------

#. Log in to the IAM console.

#. In the navigation pane, choose **Agencies**.

#. On the page that is displayed, click **Create Agency** in the upper right corner. The **Create Agency** page is displayed.

#. Set parameters by referring to :ref:`Table 1 <aom_06_0010__en-us_topic_0288483980_en-us_topic_0159938463_t7927638d398c4cc593fe522b3e57a455>`.

   .. _aom_06_0010__en-us_topic_0288483980_en-us_topic_0159938463_t7927638d398c4cc593fe522b3e57a455:

   .. table:: **Table 1** Parameters for creating an agency

      +-----------------+------------------------------------------------------------------+---------------+
      | Parameter       | Description                                                      | Example       |
      +=================+==================================================================+===============+
      | Agency Name     | Set an agency name. The agency name must be **apm_admin_trust**. | ``-``         |
      +-----------------+------------------------------------------------------------------+---------------+
      | Agency Type     | Select **Cloud service**.                                        | Cloud service |
      +-----------------+------------------------------------------------------------------+---------------+
      | Cloud Service   | Select **Application Operations Management (AOM)**.              | ``-``         |
      +-----------------+------------------------------------------------------------------+---------------+
      | Validity Period | Select **Unlimited**.                                            | Unlimited     |
      +-----------------+------------------------------------------------------------------+---------------+
      | Description     | (Optional) Provide details about the agency.                     | ``-``         |
      +-----------------+------------------------------------------------------------------+---------------+

#. Click **OK**. In the displayed dialog box, click **Authorize Agency**.

#. On the **Select Policy/Role** tab page, select **DMS UserAccess** and click **Next**.

   **DMS UserAccess**: Common user permissions for DMS, excluding permissions for creating, modifying, deleting, scaling up instances and dumping.

#. On the **Select Scope** tab page, set **Scope** to **Region-specific Projects** and select target projects under **Project [Region]**.

#. Click **OK**.
