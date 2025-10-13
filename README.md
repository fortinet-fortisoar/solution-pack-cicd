# Release Information

- **Version**:  3.1.0
- **Certified**: Yes
- **Publisher**: Fortinet
- **Compatible Version**: FortiSOAR v7.4.3 and later
- [Release Notes](./release_notes.md)
- [Upgrade Instructions](./docs/upgrade-instructions.md)

# Overview

FortiSOAR Continuous Delivery solution pack helps automate your content development workflows and deploy better quality code using a continuous and iterative process to build, test, and deploy content through Source Control.

With Continuous Integration (CI) you can integrate all your code changes into the main branch of a shared source code repository early and often, automatically testing each change when you commit or merge them. FortiSOAR Continuous Delivery helps you create a development source control where you can merge your changes and test them until you are confident that the changes are ready to be pushed to production.

Continuous Delivery (CD) takes over during the final stages to ensure that the code can be pushed to a production environment (or a staging environment if you so choose) at any time. For more granular control, you can review the code changes before pulling them from development into production or staging. Even then you can wait until you are ready to apply the changes to a production or staging environment.

<!-- The following diagram simplifies how FortiSOAR's Continuous Delivery works:

![Continuous Delivery Flowchart](./docs/res/ci-cd-flow.svg) -->

## Who Should Read This

- **Application Administrators**
  Responsible for managing the FortiSOAR production and development environments. Admins approve or reject content changes, synchronize content between environments, and ensure that only validated configurations are applied in production.

  *Example:* Approving a pull request raised by a developer and then applying the latest changes to the production environment.

- **Content Developers**
  Responsible for building and customizing FortiSOAR content such as dashboards, playbooks, reports, modules, and security settings. Developers work on CRs raised by admins, push changes to source control, and submit them for review.

  *Example:* Creating a new playbook collection in the development environment, editing the export template to include it, and pushing those changes for administrator approval.

# Next Steps 
 
| [Installation](./docs/setup.md#installation) | [Configuration](./docs/setup.md#configuration) | [Usage](./docs/usage.md) | [Contents](./docs/contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
