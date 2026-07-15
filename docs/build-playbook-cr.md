| [Home](../README.md) |
|----------------------|

## CR for Building a new Playbook

This task entails following sub-tasks:

1. Application administrator creates a new CR, in production environment, for building a new playbook. For creating a new CR refer to the [New Change Request from Production Environment](./usage.md#creating-a-new-change-request).

2. Content Developer creates a new playbook in development environment. For creating new playbooks, refer to [Introduction to playbooks](https://docs.fortinet.com/document/fortisoar/7.3.1/playbooks-guide/331279/introduction-to-playbooks). 

> [!NOTE]
> Following actions must be carried out if content developer wants to push a new playbook collection:
> 1. Content developer creates a new collection and underlying playbooks.
> 2. Content developer [edits](./editing-export-template.md) the export template. For details on editing an export template, refer to [Export Wizard](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/97786/application-editor#Export_Wizard).

3. Content developer initiates [action on the new Change Request](#working-on-the-new-change-request).

4. Application administrator [Approves & marks as complete the CR in Production environment](#approve--mark-as-complete-a-cr-in-production-environment).

5. Application administrator merges latest changes from the source control platform by [Applying Latest changes in Production environment](#apply-latest-changes-in-production-environment).

6. Application administrator verifies if the module is working as designed.

This flow is valid for all content customizations like:
- Reports
- Dashboards
- Playbooks
- Rules and channels, and
- Any other administrative and security settings.

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
