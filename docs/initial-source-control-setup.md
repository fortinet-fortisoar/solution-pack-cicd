| [Home](../README.md) |
|----------------------|

# Setting up Source Control &ndash; Initial Configuration

This section explains setting up initial configurations for a source control. Currently, **Continuous Delivery** solution pack supports the following source control platforms:

- GitHub

- GitLab

1. **Setup an organization**: Creating an organization helps keep all repositories and users under a single umbrella. Refer to these articles for creating new organizations:

    - [Creating a new organization - GitHub](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)

    - [Creating a new organization - GitLab](https://docs.gitlab.com/ee/user/organization/#create-an-organization)

2. **Create users with admin access**: Once an organization is set up, users with administrative access are required for creating private repositories and other users with different access. Refer to these articles for creating and assigning roles in an organization:

    - [Roles in an organization - GitHub](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)

    - [Members in an organization - GitLab](https://docs.gitlab.com/ee/user/project/members/index.html)

3. **Create Repositories**: Repositories can contain folders and files, images, videos, spreadsheets, and data sets - anything your project needs. The Setup Source Control process in FortiSOAR's Continuous Delivery creates repositories for you. However, you can create repositories and map them with FortiSOAR's Continuous Delivery to store and collaborate on your content customizations. Refer to these articles for creating and working with repositories:
    
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

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
