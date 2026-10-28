| [Home](../README.md) |
|----------------------|

## CR for building a new playbook

This task entails the following sub-tasks:

1. Application administrator creates a new change request (CR), in production environment, for building a new playbook. For creating a new CR, refer to [Creating a new change request](./usage.md#creating-a-new-change-request).

2. Content Developer creates a new playbook in development environment. For creating new playbooks, refer to [Introduction to playbooks](https://docs.fortinet.com/document/fortisoar/7.3.1/playbooks-guide/331279/introduction-to-playbooks).

> [!NOTE]
> Following actions must be carried out if content developer wants to push a new playbook collection:
> 1. Content developer creates a new collection and underlying playbooks.
> 2. Content developer [edits](./editing-export-template.md) the export template. For details on editing an export template, refer to [Export Wizard](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/97786/application-editor#Export_Wizard).

3. Content developer initiates [action on the new change request](./usage.md#working-on-a-new-change-request).

4. Application administrator [approves and marks the CR as complete in the production environment](./usage.md#approving-and-completing-a-cr-in-production-environment).

5. Application administrator merges latest changes from the source control platform by [applying latest changes in the production environment](./usage.md#applying-latest-changes-in-production-environment).

6. Application administrator verifies if the module is working as designed.

This flow is valid for all content customizations like:

- Reports
- Dashboards
- Playbooks
- Rules and channels
- Any other administrative and security settings

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
