| [Home](../README.md) |
|----------------------|

## CR for Building a new Module

This task entails following sub-tasks:

1. Application administrator creates a new CR, in production environment, for building a new module. For creating a new CR refer to the [New Change Request from Production Environment](./usage.md#creating-a-new-change-request).

2. Content Developer creates a new module in development environment. For creating a new module, refer to the article [Creating a New Module](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/97786/application-editor#Creating_a_New_Module).

3. Content developer adds the new module to the navigation menu. Refer to this article for [Modifying the Navigation Bar](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/97786/application-editor#Modifying_the_Navigation_bar).

4. Depending on the module and requirements, content developer may need to create new roles, or edit existing roles to assign permissions for the new module.

    - For creating new roles, refer to the article [Adding Roles](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/202940/security-management#Adding_Roles).

    - For editing permissions assigned to roles, refer to the article [Configuring Roles](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/202940/security-management#Configuring_Roles).

5. Content developer [edits](./editing-export-template.md) the export template.

6. Content developer selects module, roles, picklists, and other content created to support the new module.

7. Content developer starts [working on the new Change Request](./usage.md#working-on-a-new-change-request).

8. Application administrator [Approves & marks as complete the CR in Production environment](./usage.md#approving--completing-a-cr-in-production-environment).

9. Application administrator merges latest changes from the source control platform by [Applying Latest changes in Production environment](./usage.md#applying-latest-changes-in-production-environment).

10. Application administrator verifies if the module is working as designed.

> [!NOTE]
> Once a module is created and applied to production and development, [applying latest changes in production](./usage.md#applying-latest-changes-in-production-environment) or in [development](./usage.md#apply-latest-changes-in-development-environment) will not remove it &mdash; even if the module no longer exists in the pulled changes.

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
