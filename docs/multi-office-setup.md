| [Home](../README.md) |
|----------------------|

# Multi-office setup

This topology gives each office its own development environment while all offices share one production environment and one set of source control repositories: the Production Content Repository, the Production Settings Repository, and the Development Settings Repository. Offices never exchange content directly; every change moves through source control.

## Topology overview

The topology has one production environment, one development environment per office, and an optional staging environment shared across offices. The following flow describes how a change moves through it.

1. An admin raises a change request (CR) in the shared production environment and assigns it to a developer in a specific office.
2. That developer's office builds and pushes the change from its own development environment to the shared Production Content repository.
3. The admin reviews and approves the pull request, then applies the latest content to production.
4. Every other office pulls the same merged change into its own development environment by applying the latest content there.

## Setting up each office's development environment

Set up each office's development environment the same way as a single-office deployment: follow [Setting up the development environment](./setup-dev-env.md) on an instance dedicated to that office. The only difference in a multi-office topology is that every office's development instance must be configured with the same source control organization and the same three repository names and base branch as every other office, since they all promote content into the same production environment.

> [!NOTE]
> The playbooks do not validate that every office's configuration matches. Confirm the organization, repository names, and base branch against an existing office's configuration before setting up a new one.

## Mapping every office's developers in production

Access to the shared repositories is granted per user, not per office, so an admin must map every developer, from every office, to their source control username in the production environment. Follow the same steps regardless of which office a developer belongs to.

- [User mapping in connectors](./terminologies.md#user-mapping-in-connectors)
- [Best practices for source control and Continuous Delivery](./best-practices.md) (see item 7: each development environment user must be mapped in the production environment)

## Assigning each CR to exactly one office's dev environment

Assign each CR to a developer in a single office and let that office's development environment complete it. Do not let more than one office work on the same CR at the same time. Since the branch a CR pushes to is named after the CR's issue number and is shared across all offices, changes pushed to that branch from more than one development environment at once can conflict.

- [Creating a new change request](./usage.md#creating-a-new-change-request)
- [Best practices for source control and Continuous Delivery](./best-practices.md) (see item 14: changes for a single CR must never be pushed from multiple development environments)

## Pulling merged changes into other offices

Once a CR is approved, merged, and applied to production, every other office pulls the same merged content into its own development environment by fetching the latest changes there. This is the only way changes reach an office that did not implement them: through source control, not through any direct connection between instances.

- [Applying latest changes in development environment](./usage.md#applying-latest-changes-in-development-environment)
- [Viewing closed CRs since last deployment](./usage.md#viewing-closed-crs-since-last-deployment)

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
