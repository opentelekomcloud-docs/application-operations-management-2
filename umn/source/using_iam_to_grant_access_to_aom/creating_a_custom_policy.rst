:original_name: aom_03_0005.html

.. _aom_03_0005:

Creating a Custom Policy
========================

Custom policies can be created as a supplement to the system policies of AOM.

You can create custom policies in either of the following two ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Create a JSON policy or edit an existing one.

For details about how to create custom policies, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/en-us_topic_0274187246.html>`__. The following lists examples of common AOM custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing a user to create alarm rules

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "aom:alarmRule:create"
                  ]
              }
          ]
      }

-  Example 2: Forbidding a user to delete application discovery rules

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both Allow and Deny actions, the Deny actions take precedence over the Allow actions.

   To grant a user the **AOM FullAccess** system policy but forbid the user to delete application discovery rules, create a custom policy that denies the deletion of application discovery rules, and grant both the **AOM FullAccess** and deny policies to the user. Because the Deny action takes precedence, the user can perform all operations except deleting application discovery rules. The following is an example deny policy:

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
          "Effect": "Deny",
                        "Action": [
                              "aom:discoveryRule:delete"
                        ]
                  }
            ]
      }

-  Example 3: Defining permissions for multiple services in a policy

   A custom policy can contain actions of multiple services that are all of the project-level type. The following is an example policy containing actions of multiple services:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow",
                              "Action": [
                                      "aom:*:list",
                                      "aom:*:get",
                                      "apm:*:list",
                                      "apm:*:get"
                              ]
                      },
                      {
                               "Effect": "Allow",
                               "Action": [
                                       "cce:cluster:get",
                                       "cce:cluster:list",
                                       "cce:node:get",
                                       "cce:node:list"
                              ]
                      }
              ]
      }
