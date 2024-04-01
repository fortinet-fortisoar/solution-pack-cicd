| [Home](../README.md) |
|----------------------|

# Contents

The **Continuous Delivery** solution pack installs the following resources:

## Roles

| Role                     | Description                                                                                            |
|:-------------------------|:-------------------------------------------------------------------------------------------------------|
| Production Administrator | Responsible for change request administration in Continuous Integration and Continuous Delivery (CICD) |
| Full App Permissions     | Essentially the root user, use carefully                                                               |
| Content Developer        | Responsible for change request development in Continuous Integration and Continuous Delivery (CICD)    |

## System Views

| System View         | Description                                                                                                                                                           |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Continuous Delivery | A menu option that launches the Continuous Delivery user interface for setting up development and production environment subsequent interactions with source control. |

## Module Schemas

| Module Schema     | Description                                                                                                                                |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| People            | Adds fields to people schema to help organize information specific to users like their names and usernames related to source control platform. |
| Change Management | A schema or framework that helps organize information specific to Continuous Delivery like issue, title, description, and environment.     |

## Widgets

| Widgets                   | Description                                                                                                                                                             |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| JSON to Grid              | Renders the JSON playbook results in grid view and performs various operations on the grid.                                                                             |
| CICD Configuration Wizard | Launches a wizard that walks a user through the process of setting up source control for Continuous Delivery.                                                           |
| Record CTA Tile           | Displays the details of a module record, in Tile form, when the containing button is clicked; and also shows a Call To Action Button to Launch the Record Details Panel |
| Record Card               | Displays the module records in a card format.                                                                                                                           |

## Playbook Collections

|02 - Use Case - CICD|
|:-------------------|


| Playbook Name                                                                          | Description                                                                                                                                                                               |
|:---------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fetch Closed Requests (Issues)![icon-new](./res/icon-new.svg)                          | Fetch all closed source control requests (Issues) from Content, Production Setting and Development Setting repositories                                                                   |
| Add Source Control Repository Collaborator                                             | Add source control repository collaborator for specified repository                                                                                                                       |
| Push Content to Source Control                                                         | Clone the specified repository, apply the export template content and push to source control                                                                                              |
| Push Initial Production Environment Content                                            | Push initial Production Environment Content into source control main branch                                                                                                               |
| Setup Production Environment                                                           | Setting up the production environment involves mapping source control username with FortiSOAR users, configuring repositories, and initiating the first release.                          |
| Setup Development Environment                                                          | Setting up the development environment involves mapping source control username with FortiSOAR user, cloning the initial production content repository, and importing it into FortiSOAR.  |
| Setup CICD Environment                                                                 | Update the SVT of Change Management module as per the environment selected in CICD Configuration wizard                                                                                   |
| Set Logged in Source Control Username                                                  | Update the source control usernames in FortiSOAR logged in user record                                                                                                                    |
| Set Source Control Username                                                            | Update the source control Usernames in FortiSOAR User record                                                                                                                              |
| Save FortiSOAR Settings                                                                | Push connector configurations, SSO settings, user configurations, etc, into Source Control                                                                                                |
| Push Change to Source Control                                                          | Push specified change request content into the Source Control content repository                                                                                                          |
| Pull Latest Content from Source Control                                                | Pull latest content from Source Control repository and apply it within the FortiSOAR environment                                                                                          |
| Merge Pull Request                                                                     | Merge the specified pull request upon approval                                                                                                                                            |
| Get Issue and Source Control Details                                                   | Extract the issue and source control details based on the specified information                                                                                                           |
| Get Source Control Connector Configuration                                             | If source control connector is configured for the logged in user, then return connector configuration id else raise exception                                                             |
| Fetch Open Requests (Issues)                                                           | Fetch all open source control requests (Issues) from Content, Production Setting and Development Setting repositories                                                                     |
| Fetch Latest Changes                                                                   | Fetches the details of Latest changes available after last Sync                                                                                                                           |
| Create a Request (Issue)                                                               | Creates a Source Control Issue against the FortiSOAR Content or Settings Repository with the request content                                                                              |
| Create Repository                                                                      | Create the Public Repository for the specified repository name and base branch name in Source Control                                                                                     |
| Create Release                                                                         | Creates a release from the base branch                                                                                                                                                    |
| Create Pull Request                                                                    | Create the pull request for review and assign reviewers                                                                                                                                   |
| Configure Source Control                                                               | Create Content, Production Settings and Development Settings Repository in Source Control                                                                                                 |
| Close Change Request                                                                   | Closes the specified change request                                                                                                                                                       |
| Check Playbook is Already Running                                                      | Specify the playbook name and check whether the playbook is already running                                                                                                               |
| Get FortiSOAR Export Templates![icon-deprecated](./res/icon-deprecated.svg)            | Extract "FortiSOAR Production Environment" exported Zip File from FortiSOAR                                                                                                               |
| Add GitHub Repository Collaborator![icon-deprecated](./res/icon-deprecated.svg)        | Add GitHub repository collaborator for specified repository                                                                                                                               |
| Set Logged in GitHub Username![icon-deprecated](./res/icon-deprecated.svg)             | Update the GitHub Usernames in FortiSOAR  logged in user record                                                                                                                           |
| Set GitHub Username![icon-deprecated](./res/icon-deprecated.svg)                       | Update the GitHub Usernames in FortiSOAR User record                                                                                                                                      |
| Pull Latest Content from GitHub![icon-deprecated](./res/icon-deprecated.svg)           | Pull latest content from GitHub and apply it on production environment or development environment                                                                                         |
| Get GitHub Connector Configuration![icon-deprecated](./res/icon-deprecated.svg)        | If GitHub connector is configured for the logged in user then return connector configuration id else raise exception                                                                      |
| GitHub - Create Issue Comment![icon-deprecated](./res/icon-deprecated.svg)             | Creates an issue comment for the specified repository or user on GitHub                                                                                                                   |
| GitHub - Add Repository Collaborator![icon-deprecated](./res/icon-deprecated.svg)      | Updates a personal repository of a specified user to add a collaborator                                                                                                                   |
| GitHub - List Repository Collaborator![icon-deprecated](./res/icon-deprecated.svg)     | List repository collaborators                                                                                                                                                             |
| GitHub - Update Remote Repository![icon-deprecated](./res/icon-deprecated.svg)         | Applies changes made in a FortiSOAR file to the specified remote repository that is cloned from GitHub based on the file IRI and cloned repository path you have specified                |
| GitHub - Update Issue![icon-deprecated](./res/icon-deprecated.svg)                     | Update an issues for the specified repository or user on GitHub based on the repository name, and other input parameters you have specified                                               |
| GitHub - Push Changes![icon-deprecated](./res/icon-deprecated.svg)                     | Commits the local repository changes to the specified repository in GitHub based on the repository name, cloned repository path, and other input parameters you have specified            |
| GitHub - Merge Pull Request![icon-deprecated](./res/icon-deprecated.svg)               | Merges the specified pull request on GitHub based on the repository name, repository owner, pull request number, and other input parameters you have specified                            |
| GitHub - List Repository Issue![icon-deprecated](./res/icon-deprecated.svg)            | List an issues for the specified repository or user on GitHub based on the repository name, and other input parameters you have specified                                                 |
| GitHub - List Pull Request![icon-deprecated](./res/icon-deprecated.svg)                | Lists pull requests for the specified repository on GitHub based on the repository name, repository owner, and other input parameters you have specified                                  |
| GitHub - List Pull Request Reviews![icon-deprecated](./res/icon-deprecated.svg)        | Lists the reviews associated with the specified pull request on GitHub based on the repository name, repository owner, pull request number, and other input parameters you have specified |
| GitHub - Fetch Release![icon-deprecated](./res/icon-deprecated.svg)                    | Fetches Release from the Repo                                                                                                                                                             |
| GitHub - Delete Branch![icon-deprecated](./res/icon-deprecated.svg)                    | Delete a new branch in GitHub based on the repository name, branch name, repository owner, and other input parameters you have specified                                                  |
| GitHub - Create or Update File Content![icon-deprecated](./res/icon-deprecated.svg)    | Creates a new repository using a repository template based on the template repository, repository name, and other input parameters you have specified                                     |
| GitHub - Create Repository![icon-deprecated](./res/icon-deprecated.svg)                | Creates a new organization or authenticated user repository based on the repository name, organization name, base branch name, and other input parameters you have specified              |
| GitHub - Create Release![icon-deprecated](./res/icon-deprecated.svg)                   | Create a new release                                                                                                                                                                      |
| GitHub - Create Pull Request![icon-deprecated](./res/icon-deprecated.svg)              | Creates a pull request for the specified repository on GitHub based on the repository name, repository owner, and other input parameters you have specified                               |
| GitHub - Create Issue![icon-deprecated](./res/icon-deprecated.svg)                     | Creates an issue for the specified repository or user on GitHub based on the repository name, and other input parameters you have specified                                               |
| GitHub - Create Branch![icon-deprecated](./res/icon-deprecated.svg)                    | Creates a new branch in GitHub based on the repository name, base branch type, repository owner, and other input parameters you have specified                                            |
| GitHub - Clone Repository![icon-deprecated](./res/icon-deprecated.svg)                 | Clone the github repository                                                                                                                                                               |
| GitHub - Add Reviewers for a Pull Request![icon-deprecated](./res/icon-deprecated.svg) | Adds reviews for the specified pull request on GitHub based on the repository name, repository owner, pull request number, and other input parameters you have specified                  |
| GitHub - Add Pull Request Review![icon-deprecated](./res/icon-deprecated.svg)          | Add a review for a pull request on GitHub based on the repository name, repository owner, pull request number, and other input parameters you have specified                              |

## Connectors

| Connector  | Description                                                                                                                                    |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| GitHub     | This connector facilitates automated interactions with GitHub such as creating and managing repositories, branches, issues, and pull requests. |
| GitLab     | This connector facilitates automated interactions with GitLab such as creating and managing repositories, branches, issues, and pull requests. |
| CICD Utils | CICD Utils provides out of the box actions for CICD solution pack                                                                              |

## Record Sets

- Change Management (8)
- Export Templates (3)

## Picklists

- Change Management Environment
- Change Management Status
- Change Management Type

## Module Views

- Change Management List
- Change Management Detail
- Change Management Form
