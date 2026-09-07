:original_name: aom_03_0004.html

.. _aom_03_0004:

Creating a User and Granting Permissions
========================================

This section describes the fine-grained permissions management provided by IAM for your AOM. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own security credentials for accessing AOM resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or a cloud service to perform professional and efficient O&M on your AOM resources.

If your account does not need individual IAM users, then you may skip over this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <aom_03_0004__en-us_topic_0000002009340744_en-us_topic_0169701339_fig13279111625016>`).

Prerequisites
-------------

Before assigning permissions to user groups, you should learn about the AOM permissions listed in :ref:`Permissions Management <aom_01_0019>`. For the permissions of other services, see `Permission Description <https://docs.otc.t-systems.com/permissions/index.html>`__.

Process Flow
------------

.. _aom_03_0004__en-us_topic_0000002009340744_en-us_topic_0169701339_fig13279111625016:

.. figure:: /_static/images/en-us_image_0000002370950005.png
   :alt: **Figure 1** Process for granting AOM permissions

   **Figure 1** Process for granting AOM permissions

#. .. _aom_03_0004__en-us_topic_0000002009340744_en-us_topic_0169701339_li11838175082320:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

   Create a user group on the IAM console, and assign the **AOM ReadOnlyAccess** policy to the group.

#. `Create a user and add the user to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <aom_03_0004__en-us_topic_0000002009340744_en-us_topic_0169701339_li11838175082320>`.

#. `Log in as an IAM user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the AOM console as the created user, and verify that it only has read permissions for AOM.
