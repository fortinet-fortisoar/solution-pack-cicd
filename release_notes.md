| [Home](./README.md) |
|----------------------|

# Release notes

This page lists the changes in **Continuous Delivery** v3.2.0, relative to v3.1.0.

## v3.2.0

### Compatibility

This release changes the minimum supported FortiSOAR version.

- Minimum FortiSOAR compatibility raised from v7.4.0 to v8.0.0. Review [Upgrade instructions](./docs/upgrade-instructions.md) before upgrading.

### What's new

This release adds one new capability.

- Each change request (CR) now gets its own export template, named `Source Control (CR-<number>) - Production Content`. When a content developer pushes changes for a CR, the push uses that CR's export template instead of the shared `Source Control - Production Content` template, so one CR no longer exports content selected for another. Where the template is created and deleted depends on the deployment:

  - **Development and production on the same FortiSOAR instance**: the **Create a Request (Issue)** playbook creates the template when the CR is created. The **Close Change Request** playbook deletes it when the CR is closed.
  - **Development and production on separate FortiSOAR instances**: the template is managed on the development instance only, and no export template is created on the production instance. The **Fetch Open Requests (Issues)** playbook creates a template for each open CR that does not have one. The **Fetch Closed Requests (Issues)** playbook deletes the template of each closed CR.

  The new **Create Export Template** and **Delete Export Template** playbooks perform these actions. Per-CR templates do not isolate concurrent changes to the same object. Refer to [Best practices for source control and Continuous Delivery](./docs/best-practices.md#known-limitation-concurrent-changes-to-the-same-object).

### Bug fixes

This release includes one fix.

- The default `Source Control - Production Content` export template no longer ships with an unrelated role definition and its full permission set bundled into it.