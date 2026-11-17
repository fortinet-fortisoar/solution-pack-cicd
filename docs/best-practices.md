| [Home](../README.md) |
|----------------------|

## Best practices for source control and Continuous Delivery

Apart from best practices around source control like branching and merging strategies, committing code frequently with clear commit messages, automating the build process, and using a deployment pipeline for consistent and reliable releases, the following pointers help avoid common pitfalls.

1. While creating repos using playbooks, ensure that your preferred source control platform's connector is configured.

    - Credentials used in the configuration must have sufficient privileges to create private repos in the specified organization.

    - Your preferred source control platform's username specified during configuration must be mapped with the user who is setting up the Source Control.

2. For repos with restricted merge access, the logged-in user must have sufficient privileges to make the initial commit without creating a pull request (PR).

3. When mapping existing repos during Continuous Delivery's **Setup Source Control** process, ensure the **Issues** and **Merge commits** options are enabled for these existing repos.

    | ![Enabling Issues on a repository](./res/repo-settings-enable-issues.png) | ![Enabling merge commits on a repository](./res/repo-settings-enable-merge-commits.png) |
    |:-----------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------:|
    |                    Enabling Issues on a repository                    |                    Enabling merge commits on a repository                    |

4. Users and their tokens must have sufficient privileges for following actions:

    - Creating or closing a change request

    - Creating or deleting a branch

    - Merging a pull request (PR)

5. After applying latest changes [in the production environment](./usage.md#applying-latest-changes-in-production-environment) or [in the development environment](./usage.md#applying-latest-changes-in-development-environment), perform the following actions for optimum performance:

    - Refresh the FortiSOAR page

    - Logout and login

    - For a role change or addition, ensure the role is assigned to the appropriate user

6. In case of conflicts in a pull request (PR), resolve the conflict on the source control platform before merging the PR.

7. Each development environment user must be mapped with their preferred source control platform's username in the *production* environment. 

8. Base Branch must never be deleted.

9. The global variable `cicd_env` must never be modified or deleted.

10. When setting role permissions, never allow **Delete** permission to the **Change Management** module.

11. Do not modify **Change Management** module's Service View Template (SVT).

12. Do not create a PR before pushing code to the related branch

13. Content developer must never be the PR reviewer.

14. Changes related to a single change request (CR) must never be pushed from multiple development environments.

15. After the action **Apply Latest Content** is run on a development or production environment, an `fsrimport-xxx` file (for example, `fsrimport-381e5a85-ccb5-4407-b5ea-97d294bb3a5e`) is created in the `/tmp` directory.

    These files are intended for deletion. To automate the process, you can establish a cron job to remove these files.

### Known limitation: concurrent changes to the same object

Per-CR export templates stop one CR from exporting content selected for another. They do not isolate two CRs that change the same object.

<!-- DEV REVIEW: Limitation and recommendation sourced from the design document, not from code. Confirm, or raise an objection. -->

- FortiSOAR exports content as whole objects, not as incremental changes. This applies to playbook collections, dashboards, reports, service view templates (SVTs), modules, layouts, and connector configurations.
- If two CRs change the same object, for example, each adds a different playbook to the same playbook collection, each CR exports the complete object.
- The CR merged last overwrites the changes of the earlier CR to that object.
- The solution pack does not provide object-level locking, object-level merge, or conflict detection during push.

To avoid lost changes, do not assign concurrent CRs that change the same object to different content developers.

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|