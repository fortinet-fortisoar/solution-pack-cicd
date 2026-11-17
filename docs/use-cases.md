| [Home](../README.md) |
|----------------------|

# Use cases

This page describes the scenarios the **Continuous Delivery** solution pack is built to support, and links to the task documentation that implements each one. It does not introduce new procedures; follow the linked pages to carry out the steps.

## Promoting content from development to production with review gates

A content developer builds and tests a change in the development environment, then submits it for review. The application administrator, who cannot approve their own submission, reviews the pull request on the source control platform and approves it in FortiSOAR before the change reaches production. This keeps every production change behind a second set of eyes.

- [Lifecycle of a change request (CR)](./usage.md#lifecycle-of-a-change-request-cr)
- [Approving and completing a CR in production environment](./usage.md#approving-and-completing-a-cr-in-production-environment)
- [Best practices for source control and Continuous Delivery](./best-practices.md) (see item 13: a content developer must never be the PR reviewer)

## Maintaining an audit trail for change requests

Every change request an admin raises in production is linked, end to end, to a source control issue, the pull request that resolves it, and the reviewer who approved it. An admin or auditor can follow this chain from the **Continuous Delivery** menu in FortiSOAR or directly on the source control platform.

- [Lifecycle of a change request (CR)](./usage.md#lifecycle-of-a-change-request-cr)
- [Creating a new change request](./usage.md#creating-a-new-change-request)
- [Viewing closed CRs since last deployment](./usage.md#viewing-closed-crs-since-last-deployment)

## Backing up environment settings

An admin versions system settings, such as system views, LDAP, SSO, RADIUS, and other application configuration, to the Production Settings or Development Settings repository so they can be reviewed, compared, and restored like any other source-controlled content.

- [Saving development settings](./usage.md#saving-development-settings)
- [Applying latest changes in production environment](./usage.md#applying-latest-changes-in-production-environment) (choose *Production Settings* from the drop-down)
- [Installation](./setup.md#installation) (see Source Control Repositories for what each of the three repositories stores)

> [!NOTE]
> The default export templates back up system settings, LDAP, RADIUS, TOKEN, HA, SSO, syslog, and proxy configuration, and views. They do not include connector configurations by default. To back up connector configurations too, edit the export template first: see [Including connector installation and configuration in source control](./connector-inst-config-git.md).

## Cloning a new instance from production content

A new FortiSOAR instance, whether it's a development instance, a staging instance, or a replacement production instance, is bootstrapped by cloning the shared Production Content repository rather than being built from scratch.

- [Setting up the development environment](./setup-dev-env.md)
- [Setting up the staging environment](./setup-staging-env.md)

## Validating content in a staging environment

A staging environment is optional. When configured, it gives admins and testers a production-like instance to validate changes in before those same changes are applied to the real production instance.

- [Setting up the staging environment](./setup-staging-env.md)
- [Understanding the environments](./usage.md#understanding-the-environments) (see Staging environment (optional))

## Running multiple development environments against one production environment

Several developers, or separate teams, can each work from their own development instance while all of them promote content to the same production instance through the same source control organization. Each content developer's source control username is mapped in the production environment so their commits and pull requests are attributed correctly.

- [Setting up the development environment](./setup-dev-env.md)
- [Best practices for source control and Continuous Delivery](./best-practices.md) (see items 7 and 14: map every developer's username in production, and never push a single CR's changes from more than one development environment)

## Setting up a multi-office topology

Each office runs its own development environment, all offices and the shared production environment use the same source control organization and the same three repositories, and offices exchange changes only through source control, never directly between instances.

- [Multi-office setup](./multi-office-setup.md)

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
