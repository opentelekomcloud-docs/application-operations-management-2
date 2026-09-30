:original_name: aom_04_0022.html

.. _aom_04_0022:

Introduction
============

You can use Identity and Access Management (IAM) for fine-grained permissions management of your AOM. If your account does not need individual IAM users, you can skip this topic.

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on AOM.

You can grant users permissions by using roles and policies. Roles are provided by IAM to define service-based permissions that match users' job responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   If you want to allow or deny the access to an API, use policy-based authorization.

Your account has all the permissions required to call all APIs, but IAM users under your account must be assigned the required permissions. The required permissions are determined by the actions supported by the API. Only users with the policies allowing for those actions can call the API successfully. For example, if an IAM user wants to query metrics using an API, the user must have been granted permissions that allow the **aom:metric:get** action.

Supported Actions
-----------------

AOM provides system-defined policies that can be directly used in IAM. You can also create custom policies to supplement system-defined policies for more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: actions defined in custom policies.
-  APIs: REST APIs that can be called by a user who has been granted specific permissions.
-  Actions: specific operations that are allowed or denied in a custom policy.
-  IAM projects/Enterprise projects: the authorization scope of a custom policy. A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions for both IAM and enterprise projects can be used and applied for both IAM and Enterprise Management. Policies that contain actions only for IAM projects can be used and applied to IAM only. Administrators can check whether an action supports IAM projects or enterprise projects in the action list. .

AOM supports the following actions that can be defined in custom policies:

-  :ref:`Alarm APIs <aom_04_0036>`: includes the actions supported by alarm APIs, such as the API for querying alarms.
-  :ref:`Monitoring APIs <aom_04_0033>`: includes the actions supported by monitoring APIs, such as the API for querying metrics.
-  :ref:`Log APIs <aom_04_0035>`: includes the actions supported by log APIs, such as the API for querying logs.
