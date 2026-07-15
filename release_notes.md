| [Home](./README.md) |
|----------------------|

# What's New

This release brings significant improvements to the *Change Management* process in FortiSOAR's **Continuous Delivery** solution pack. Instantly noticeable smoother workflows, clearer visibility into change requests (CRs), and enhanced control over applying content changes across environments. The enhancements ensure that CR lifecycle management, from development to production, is more transparent and less error-prone.

---

## Enhancements

### Wizard Improvements

- Only **GitHub** and **GitLab** are now available in the **Select Your Source Control** option, simplifying platform selection for Continuous Delivery setup.

- The wizard now waits for the **Setup CICD Environment** playbook to complete before proceeding to the Finish step, ensuring that the source control environment is fully prepared before deployment.

### Change Log Visibility

- The **Apply Latest Content** feature in both production and development environments now computes and displays a **change log**.

- Analysts can clearly see what changes are being merged before they are applied, reducing the risk of surprises in production.

### New Tracking Fields in Change Management

- Added **Last Commit ID** and **Commit Status** fields.

- These fields allow analysts to trace exactly which commit was last applied and whether it succeeded, making CR tracking more reliable.

### Task Management Improvements

The following improvements give analysts more flexibility in managing workflows:

- A **Reset Task** button appears when the task is completed or is in progress.

- An **Abort** button to cancel the change request being created; as simply closing the modal may keep the associated playbook *active*.

### Source Control Settings

- A new card **Source Control Settings** under both *Production* and *Development* tabs helps manage exported content such as playbooks, module definitions, connectors, and related components to streamline updates and ensure critical components are version-controlled.

  This card features a new **Edit Export Template** button that helps export the following:

  - **Production Settings** from the *Production* tab

  - **Production Content** and **Development Settings** from the *Development* tab

- A new button **Update Configuration Parameters** helps edit the source control configuration parameters after the *Production* and *Development* environments have been set up.

### Review and Apply Latest Content

- A new button in both *Production* and *Development* environments triggers an **import wizard** that guides analysts through applying content changes.

- The wizard applies both *Production Content* and *Production Settings* safely, with a clear preview of what will change.

### Improved PR Workflow

- When submitting a PR for review, analysts can now **select reviewers from a drop-down list of Git users** rather than typing usernames manually.

### Miscellaneous

- Task progress notifications now include more information to give better context on the tasks at hand and reduce navigation overhead. For example: **direct links** are included when a repository or PR is created.

- A new **CR Status** column under issues shows the lifecycle state of each CR, improving at-a-glance tracking.

- Multiple pre-checks added as part of error handling in various Continuous Delivery operations such as:

  - Repository creation - Repo creation is skipped if the repository already exists.

  - PR review - The creator of a PR can no longer be the reviewer.

  - Create issue - The playbook easily handles any special characters in the title and description fields of an issue.



---

## Bug Fixes

- Fixed the following issues:

  - Users could not create another production content repository when setting up multiple production environments
  - Production/Development tabs appeared prematurely before source control setup.
  - PR links and their statuses were not visible in the UI when multiple issues were listed.
  - Reviewer names caused submission errors in push/PR workflows.
  - PR submission failed if a PR already existed for the CR.
  - Source control sync status retrieval did not retrieve user context.
  - Legacy HTML code and Key Store dependencies were removed for cleaner execution.

Together, these fixes reduce friction and ensure analysts can rely on predictable CR workflows.

---

## Why Upgrade Now

With this release, SOC analysts gain **greater clarity in CR tracking**, **fewer blockers in workflows**, and **more control when applying content safely**. If you're still on an earlier version, upgrading ensures smoother day-to-day operations and prevents errors during critical change rollouts.

Refer to [Upgrade Instructions](./docs/upgrade-instructions.md) for more information.
