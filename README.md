# Release information

This section summarizes the solution pack's release details.

- **Version**: 3.2.0
- **Certified**: Yes
- **Publisher**: Fortinet
- **Compatible Version**: FortiSOAR v8.0.0 and later
- [Release notes](./release_notes.md)
- [Upgrade instructions](./docs/upgrade-instructions.md)

# Overview

FortiSOAR Continuous Delivery solution pack helps automate your content development workflows and deploy better quality code using a continuous and iterative process to build, test, and deploy content through Source Control.

With Continuous Integration (CI) you can integrate all your code changes into the main branch of a shared source code repository early and often, automatically testing each change when you commit or merge them. FortiSOAR's Continuous Delivery helps you create a development source control where you can merge your changes and test them until you are confident that the changes are ready to be pushed to production.

Continuous Delivery (CD) takes over during the final stages to ensure that the code can be pushed to a production environment (or a staging environment if you so choose) at any time. For more granular control, you can review the code changes before pulling them from development into production or staging. Even then you can wait until you are ready to apply the changes to a production or staging environment.

<!-- The following diagram simplifies how FortiSOAR's Continuous Delivery works:

![Continuous Delivery Flowchart](./docs/res/ci-cd-flow.svg) -->

## Use cases

This solution pack supports the following use cases. See [Use cases](./docs/use-cases.md) for detailed scenarios and links to the relevant setup and usage documentation.

- [Promoting content from development to production with review gates](./docs/use-cases.md#promoting-content-from-development-to-production-with-review-gates): route every change through a pull request that a second person must approve before it reaches production.
- [Maintaining an audit trail for change requests](./docs/use-cases.md#maintaining-an-audit-trail-for-change-requests): trace a production change back through its change request, source control issue, pull request, and reviewer.
- [Backing up environment settings](./docs/use-cases.md#backing-up-environment-settings): version system settings such as LDAP, SSO, and RADIUS configuration in source control.
- [Cloning a new instance from production content](./docs/use-cases.md#cloning-a-new-instance-from-production-content): bootstrap a new FortiSOAR instance from the shared production content repository.
- [Validating content in a staging environment](./docs/use-cases.md#validating-content-in-a-staging-environment): add an optional pre-production instance to review changes before they reach production.
- [Running multiple development environments against one production environment](./docs/use-cases.md#running-multiple-development-environments-against-one-production-environment): let several developers or teams work from separate development instances that all promote content to the same production instance.
- [Setting up a multi-office topology](./docs/use-cases.md#setting-up-a-multi-office-topology): give each office its own development environment while sharing one production environment and one set of source control repositories.

## Who should read this

This solution pack is intended for the following audiences.

- **Application Administrators**
  Responsible for managing the FortiSOAR production and development environments. Admins approve or reject content changes, synchronize content between environments, and ensure that only validated configurations are applied in production.

  *Example:* Approving a pull request raised by a developer and then applying the latest changes to the production environment.

- **Content Developers**
  Responsible for building and customizing FortiSOAR content such as dashboards, playbooks, reports, modules, and security settings. Developers work on CRs raised by admins, push changes to source control, and submit them for review.

  *Example:* Creating a new playbook collection in the development environment, editing the export template to include it, and pushing those changes for administrator approval.

# Next steps

| [Installation](./docs/setup.md#installation) | [Configuration](./docs/setup.md#configuration) | [Usage](./docs/usage.md) | [Contents](./docs/contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
