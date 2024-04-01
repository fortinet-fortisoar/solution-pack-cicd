# Release Information

- **Version**:  3.0.0
- **Certified**: Yes
- **Publisher**: Fortinet
- **Compatible Version**: FortiSOAR v7.4.3 and later
- [**Release Notes**](./release_notes.md)
- [**Upgrade Instructions**](./docs/upgrade-instructions.md)

# Overview

FortiSOAR Continuous Delivery solution pack helps automate your content development workflows and deploy better quality code using a continuous and iterative process to build, test, and deploy content through Source Control.

With Continuous Integration (CI) you can integrate all your code changes into the main branch of a shared source code repository early and often, automatically testing each change when you commit or merge them. FortiSOAR Continuous Delivery helps you create a development source control where you can merge your changes and test them until you are confident that the changes are ready to be pushed to production.

Continuous Delivery (CD) takes over during the final stages to ensure that the code can be pushed to a production environment (or a staging environment if you so choose) at any time. For more granular control, you can review the code changes before pulling them from development into production or staging. Even then you can wait until you are ready to apply the changes to a production or staging environment.

The following diagram simplifies how FortiSOAR's Continuous Delivery works:

![Continuous Delivery Flowchart](./docs/res/ci-cd-flow.svg)

## Intended Audience

This document is meant for content developers and FortiSOAR administrators who build FortiSOAR content to suit their daily requirements. Customizations to FortiSOAR content can be pushed to source control in the development environment. After ironing out any issues with customizations and when confident about the custom content, the same can be pushed to the production source control to be delivered/deployed on the production FortiSOAR instance.

# Terminology

This section provides a comprehensive list of specialized terms and definitions used in this document. It serves as a reference guide to ensure that any communication regarding FortiSOAR's **Continuous Delivery** solution pack is clear and consistent. The section may include definitions, abbreviations, acronyms, and jargon that are unique to this solution pack.

This terminology section may be regularly updated to reflect any changes or additions to the terms used throughout this document.

1. **Content**: Content or FortiSOAR content includes customizable components like playbooks, connectors, roles, and module schemas to name a few.

2. **Production Settings**: Production settings are system views, application configuration, environment variables, account configuration, LDAP, SSO, and RADIUS configuration in a production environment.

3. **Development Settings**: Development settings are system views, application configuration, environment variables, account configuration, LDAP, SSO, and RADIUS configuration in a development environment.

4. **FortiSOAR Admin**: A FortiSOAR admin has administrative rights on any FortiSOAR instance. For more information on users and roles, refer to [Tasks & Permissions](https://docs.fortinet.com/document/fortisoar/7.3.1/administration-guide/249178/overview#Tasks_and_Permissions) in  FortiSOAR Administration Guide.

5. **Source Control**: Source control (or version control) is the practice of tracking and managing changes to code. Source control management (SCM) systems provide a running history of code development and help resolve conflicts when merging contributions from multiple sources. Common examples of source control are **GitHub** <img src="./docs/res/github.png" width="20"> or **GitLab** <img src="./docs/res/gitlab.png" width="20">.

6. **Source Control Production Admin**: A source control administrator has rights to create users, assign permissions, create, and manage repositories in an organization. Refer to following articles that details various user roles and access:

    - [Roles in an organization - **_GitHub_**](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)

    - [Roles in an organization - **_GitLab_**](https://docs.gitlab.com/ee/user/project/members/index.html)

# Initial Source Control Configuration

This section explains setting up initial configurations for a source control. Currently, Continuous Delivery solution pack supports the following source control platforms:

- **GitHub** <img src="./docs/res/github.png" width="20">

- **GitLab** <img src="./docs/res/gitlab.png" width="20">

1. **Setup an organization**: Creating an organization helps keep all repositories and users under a single umbrella. Refer to these articles for creating new organizations:

    - [Creating a new organization - GitHub](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)

    - [Creating a new organization - GitLab](https://docs.gitlab.com/ee/user/organization/#create-an-organization)

2. **Create users with admin access**: Once an organization is set up, users with administrative access are required for creating private repositories and other users with different access. Refer to these articles for creating and assigning roles in an organization:

    - [Roles in an organization - GitHub](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)

    - [Members in an organization - GitLab](https://docs.gitlab.com/ee/user/project/members/index.html)

3. **Create Repositories**: Repositories can contain folders and files, images, videos, spreadsheets, and data sets – anything your project needs. The Setup Source Control process in FortiSOAR's Continuous Delivery creates repositories for you. However, you can create repositories and map them with FortiSOAR's Continuous Delivery to store and collaborate on your content customizations. Refer to these articles for creating and working with repositories:
    
    - [Creating and working with repositories - GitHub](https://docs.github.com/en/get-started/quickstart/create-a-repo)

    - [Creating and working with repositories/projects - GitLab](https://docs.gitlab.com/ee/user/project/#create-a-blank-project)

4. **Branching**: You can create branches so your changes do not affect the production content, and when ready can be merged into the main branch. Refer to these articles on Creating branches in a repository

    - [Creating branches in a repository - GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)

    - [Creating branches in a repository - GitLab](https://docs.gitlab.com/ee/user/project/repository/branches/)

5. **Staging, Committing, and pushing changes**: Refer to these articles on contributing and collaborating:

    - [Contributing and collaborating on GitHub using GitHub Desktop](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop)

    - [Contributing and collaborating on GitLab](https://docs.gitlab.com/ee/tutorials/make_first_git_commit/index.html#commit-and-push-your-changes)

6. **Working with Personal Access Tokens**: Personal access tokens help avoid entering sensitive information like passwords. You can assign only relevant rights to your access token. GitHub  and GitLab connectors in FortiSOAR require a personal access token to be entered during configuration. Refer to these articles for generating and using personal access tokens:

    - [Accessing GitHub using Personal Access Token (Classic)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#personal-access-tokens-classic)

    - [Accessing GitLab using Personal Access Token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)

7. **Invite Collaborators**: Collaborators have write access to the repositories to which they are invited. Collaborators must accept the invitation from GitHub's or GitLab's user interface to begin contributing.

## Pluggable Source Control

Pluggable source control is the ability of the **Continuous Delivery** solution pack to integrate with source control systems without the need for extensive customization or development. Here's how the implementation of pluggable source control looks in FortiSOAR:

- **Pre-built Integrations**: The platform seamlessly integrates with popular source control platforms such as GitHub and GitLab. These integrations are easily configurable through the **Continuous Delivery** solution pack's interface, requiring minimal setup.

- **Configuration Options**: Users can configure connection settings, authentication credentials, and other parameters specific to their source control platforms using source control connectors like GitHub and GitLab.

- **Functionality**: Once configured, users can perform common and complex version control operations directly from within FortiSOAR. This includes tasks such as:
    - Cloning repositories
    - Pushing changes
    - Pulling updates
    - Listing issues and open PRs

- **Flexibility**: The pluggable source control is scalable and flexible enough to accommodate different use cases and environments. This includes support for both cloud-based (GitHub) and self-hosted (GitLab) source control platforms.

- **Security**: FortiSOAR's trusted encryption of sensitive data like authentication tokens and access control mechanisms are built into the integrations to ensure the safety and integrity of assets stored in version control repositories.

By offering pluggable source control capabilities, FortiSOAR empowers organizations to seamlessly integrate their security orchestration and automation workflows with their preferred source control platforms, streamlining collaboration, enhancing productivity, and ensuring availability of FortiSOAR customizations across organizations' geographical locations.

For more information on developing **Pluggable Source Control** with FortiSOAR's **Continuous Delivery** solution pack, refer [Pluggable Source Control](./docs/pluggable-source-control.md).

# Next Steps 
 
| [Installation](./docs/setup.md#installation) | [Configuration](./docs/setup.md#configuration) | [Usage](./docs/usage.md) | [Contents](./docs/contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
