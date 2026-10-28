| [Home](../README.md) |
|----------------------|

# Usage

This section explains how to use the **Continuous Delivery (CI/CD) solution pack** in FortiSOAR for managing content changes, synchronizing environments, and integrating with external source control platforms like GitHub or GitLab. It walks through the complete lifecycle of a Change Request (CR), from creation to approval, and shows how administrators and developers can collaborate effectively to manage FortiSOAR content in a controlled, versioned manner.

The instructions in this guide are scenario-driven, focusing on practical workflows such as creating new playbooks or modules, exporting settings, or applying changes from source control to production environments. Each section highlights the actions required by specific roles to maintain separation of duties and ensure smooth content delivery.

## Understanding the environments

The CI/CD solution pack for FortiSOAR uses a two-tier environment baseline: **Development** and **Production**. You can optionally add a **Staging** environment as an intermediate validation layer between development and production. Each environment interacts with source control to enable controlled, auditable changes.

### Production environment

The production environment is your "live" FortiSOAR system handling real security incidents. Changes here must be deliberate and thoroughly tested to avoid disrupting operations.

Admins raise **Change Requests (CRs)** in production when new customizations or updates are required. These CRs are synchronized with source control and assigned to developers for implementation.

*Example:* An admin raises a CR to add a new phishing triage playbook. The CR is sent to the development team via source control.

### Development environment

The development environment is a sandbox where developers implement and test new content or configuration changes. Changes are iterative and experimental here.

Once development is complete, changes are submitted as **Pull Requests (PRs)** in source control. Admins review and approve these PRs before applying changes to production.

*Example:* A developer creates a new phishing triage playbook, tests it in development, and submits a PR for review.

### Staging environment (optional)

A staging environment is not required, but you can set one up as an intermediate validation layer between development and production. Its role depends on perspective:

- **For development:** staging is "Production": developers deploy their tested changes here to check that they work in an environment similar to the actual production instance.
- **For production:** staging is "Development": admins can see changes applied here before they reach live production, supporting a safer rollout.

*Example:* After testing a new playbook in development, a developer deploys it to staging. Admins and other testers validate the playbook in staging before approving its application in production.

### Flow between environments

Changes move through the environments in this sequence:

1. **Production to development:** Admins raise CRs in production that are implemented in development.
2. **Development to production:** Developers push changes from development to source control, where admins review and approve them before they reach production.
3. **Optional staging step:** If a staging environment is configured, developers push changes to staging first, and admins validate them there before the same changes are applied to production.

This baseline keeps production stable while supporting continuous development and, when needed, an extra validation layer before deployment.

Here's a diagram and table that illustrate the environment flow:

![](./res/environment-flow-diagram.svg)

### Environment roles table

The following table summarizes the role each environment plays and who is responsible for it.

| Environment            | Primary role                                         | Perspective | Example actions                                                                                     |
|-------------------------|-------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------|
| **Production**          | Live incident handling                                | Admin       | Raise CRs, approve and merge changes, apply latest content                                            |
| **Development**         | Sandbox for implementing changes                      | Developer   | Build new playbooks, dashboards, modules; push changes to source control                              |
| **Staging (optional)**  | Validation layer between development and production   | Hybrid      | Test developer changes in a near-production setting before final rollout; QA by admins and testers    |

## Lifecycle of a change request (CR)

This section explains how a change request (CR) moves through the Continuous Delivery workflow, from creation in FortiSOAR to deployment in the production environment. The workflow ensures that content developed in a **Development Environment** is reviewed, tested, and safely applied to the **Production Environment**. A staging environment, if configured, acts as an intermediate sandbox that provides a "production-like" testing space before final deployment.

![Lifecycle of a change request](./res/CR-life-cycle.svg)

### Steps in the CR lifecycle

The CR lifecycle includes the following steps:

1. **Create a Change Request (Production Environment)**
   The application administrator creates a new CR in FortiSOAR's **Production Environment**.

   - Refer to [Creating a new CR](./usage.md#creating-a-new-change-request).
   - The CR automatically appears as a new issue under **Issues** in the source control repository for the production content.
   - An export template named `Source Control (CR-<number>) - Production Content` is created for the CR. When development and production share one FortiSOAR instance, it is created with the CR. When they are separate instances, it is created on the development instance when open CRs are fetched.

2. **Build the Content (Development Environment)**
   The content developer works on the CR in the **Development Environment**, implementing the requested changes.

   - If required, the developer edits the CR's export template to include new playbooks, dashboards, rules, or other content.

> [!Warning]
> Do not delete or rename existing export templates, including CR export templates. The playbooks find a CR's export template by name and delete it automatically when the CR is closed. Cloning an export template with the same name as an existing one can cause merge conflicts and data loss.

3. **Push Changes to Source Control (Development Environment)**
   The developer selects the CR in FortiSOAR and clicks **Push Changes to Source Control**.

   - A new branch is created on the source control platform containing the changes from this CR.
   - The changes are committed and pushed to the branch automatically.
   - The push exports only the content selected in the CR's export template.

4. **Submit Changes for Review (Development Environment)**
   The developer selects the CR again and clicks **Submit Changes for Review**.

   - This action creates a pull request (PR) on the source control platform with the title and reviewers specified by the developer.

5. **Review the Pull Request (Source Control Platform)**
   CRs with changes appear under the **Pull Request** column in FortiSOAR.

> [!NOTE]
> Reviewers must log in to the source control platform to view the `diff`. Without logging in, FortiSOAR cannot display the PR differences.

6. **Approve Changes (Production Environment)**
   The application administrator reviews and approves the PR in FortiSOAR.

   - Approving the CR merges the PR into the main branch.
   - The CR branch is automatically deleted.

7. **Mark CR as Complete (Production Environment)**
   The administrator selects the CR again and clicks **Mark as Complete**.

   - This closes the CR in FortiSOAR and the source control platform.
   - The CR's export template is deleted. When development and production are separate instances, it is deleted from the development instance when closed CRs are fetched.

8. **Apply Latest Content to Production Environment**
   Once the CR is approved and completed, the application administrator clicks **Apply Latest Content** in FortiSOAR.

   - This initiates a `git merge` of the changes on the source control platform with the production instance.
   - If a **Staging Environment** is configured, the merge can first be applied there for validation before final production deployment.

> [!TIP]
> Always validate content in a staging environment (if available) before applying to production to catch potential issues early.

## Creating a new change request

You can raise a change request (CR) from within the FortiSOAR's production environment and assign it to a content developer for further action. To create a new CR and assign it to a content developer:

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Select the tab **Production**.

3. Click <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-add-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-add-dark.svg"><img alt="" src="./res/icon-add-dark.svg"></picture> **Create New Request**.

4. Enter a **Summary** and an appropriate **Description** for the CR.

5. Select a user from the **Assignee** drop-down to assign the CR.

6. Click **Submit** to save and submit the CR for further action.

The raised CR appears under **Issues** on the source control platform under your organization's Production Content repository and under the **Continuous Delivery** menu for Application Administrators.

## Working on a new change request

> [!TIP]
> Once the *Development* environment is set up, click the card **Apply Latest Content** to make the development instance a clone of *Production* instance (Required if the production and development FortiSOAR instances are separate).

The raised CR also appears under the **Continuous Delivery** menu for the Content Developer to whom the issue is assigned. Content developers see only the CRs assigned to them.

<!-- DEV REVIEW: Assignee-based CR visibility is not implemented in any playbook. Confirm in widget code, or raise an objection. -->

Use the refresh icon <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-refresh-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-refresh-dark.svg"><img alt="" src="./res/icon-refresh-dark.svg"></picture>, if the CR does not appear automatically.

After content developers are done making the customizations to address the CR raised in FortiSOAR:

1. [Edit the CR's export template](./editing-export-template.md), `Source Control (CR-<number>) - Production Content`, to include the content created. Only the export templates of the developer's open CRs are available for pushing.

   <!-- DEV REVIEW: Push selects the CR export template by branch name. Restricting templates to the developer's open CRs is not found in playbooks. Confirm in widget code, or raise an objection. -->

   For example, if the content developers have built a new Dashboard, they need to edit the CR's export template, select **Module** and click **Continue**, select the newly created Dashboard on the next screen, and click **Save**. This action ensures that the new dashboard is part of the content to be pushed to source control.

2. Select the CR and click **Push Changes**. The following tasks are performed:

   1. A branch containing the changes of this CR is created on the source control platform. The content is exported using the CR's export template.

   2. The changes are committed and pushed to the new branch.

   3. A prompt asks the content developer to specify a **Summary** (mandatory) and **Description** (optional) of the commit message.

3. Select the CR again and click **Submit for Review**. Creation of a PR is initiated.

4. Specify a **Title** of the PR.

5. Select **Reviewers Name** from the list. Content developer is not listed as the reviewer.

## Approving and completing a CR in production environment

The CR submitted for review needs approval of the application administrator in FortiSOAR. The application administrator now has to approve, merge, and mark the changes as complete in production environment.

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Select the tab **Production**.

3. CRs with changes appear with a PR name under the column **Pull Request**.

> [!NOTE]
> The reviewers have to log in to the source control platform to view the comparable differences (`diff`).

4. Select the CR in FortiSOAR and click **Approve Changes**. This merges the PR into the main branch and deletes the CR branch.

5. Select the CR again and click **Mark as Complete** to close the issue from FortiSOAR and the source control platform. This also deletes the CR's export template.

## Applying latest changes in production environment

Application administrators may want to merge the customizations on the source control platform on the main branch to production instance on FortiSOAR.

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Select the tab **Production**.

3. Click the tile **Apply Latest Content**.

4. From the drop-down choose whether to apply the *Production Content* or *Production Settings*.

5. Click the button **Submit**.

6. Click **Yes** on the confirmation to initiate a git merge of content on the source control platform with content on the FortiSOAR instance.

Once the changes are applied, logout and login again to view published changes.

## Saving development settings

To back up development settings, such as connector configurations, SSO settings, and user configurations, to source control:

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Select the tab **Development**.

3. Click the tile **Save Development Settings** to initiate export of development settings like connector configurations, SSO settings, and user configurations to the source control platform in the repository mapped with FortiSOAR Development Settings.

## Applying latest changes in development environment

Application administrators may want to merge the customizations on the source control platform on the main branch to development instance on FortiSOAR.

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Select the tab **Development**.

3. Click the tile **Apply Latest Content**.

4. From the drop-down choose whether to apply the *Production Content* or *Development Settings*.

5. Click the button **Submit**.

6. Click **Yes** on the confirmation to initiate a git merge of content on the source control platform with content on the FortiSOAR instance.

Once the changes are applied, logout and login again to view published changes.

## Viewing closed CRs since last deployment

This section explains how to get a list of closed change requests (CRs) since **Apply Latest Content** was last run in the production environment.

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Click **Apply Latest Content** tile under the **Production** tab.

3. Click **Fetch Latest Changes** button from the lower-left of the screen to get the list of issues resolved since the last applied change.

# Additional resources

The following resources cover related setup tasks, terminology, and example workflows referenced throughout this guide.

- [Terminologies](./terminologies.md): short description of commonly used terms across the document.

- [Setting up source control: initial configuration](./initial-source-control-setup.md): checklist of basic configurations that must be in place for the most efficient usage of **Continuous Delivery** solution pack.

- [Best practices](./best-practices.md): pointers to avoid common pitfalls when working with source control.

- [CR for building a new playbook](./build-playbook-cr.md): use this example flow to create playbooks.

- [CR for building a new module](./build-module-cr.md): use this example flow to create modules.

- [Including connector installation and configuration in source control](./connector-inst-config-git.md): steps to include connector installation and configuration under source control.

- [Exporting sample alerts/incidents from prod environment](./export-alerts-incidents-from-prod.md): export sample alerts or incidents from a production environment to work with and test.

- [Editing the export template](./editing-export-template.md): edit export template to manage what gets exported to a production or a development environment.

- [Multi-office setup](./multi-office-setup.md): set up one shared production environment with a development environment per office.

- [Upgrade instructions](./upgrade-instructions.md): important to review before, and after, upgrading the **Continuous Delivery** solution pack.

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|---------------------------|