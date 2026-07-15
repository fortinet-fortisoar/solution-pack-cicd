| [Home](../README.md) |
|----------------------|

## Setup Production Environment

You can setup source control management through playbooks, automatically, or by pre-creating repositories on your preferred source control platform and linking them to FortiSOAR Continuous Delivery solution pack.

To setup your preferred source control platform and create repositories using playbooks:

1. Select **Continuous Delivery** from the FortiSOAR menu.

2. Click the button **Setup Source Control**.

3. Click the button **Setup Production Environment**.

4. Enter the source control username with which to map your logged in user and click **OK**.

5. Enter the Source Control details:

    ![Source Control Details Modal](./res/source-control-details.png)

    1. Enter the Organization's name as created on your preferred source control platform.

    2. Enter the repository names to be created under the specified organization. To accept the auto-populated suggested name, leave the fields as-is.

    3. Enter the **Base Branch Name** to be created under the specified repositories. To accept the auto-populated suggested name, leave the field as-is.

    4. Click **Setup** to proceed.

6. Click the button **Create Repositories** to let the playbooks automatically create the repos (repositories) and the specified branch in each repo.

    1. Click the button **I have the repositories** if you have already created the repositories, with the exact same names as specified in the earlier step, on your preferred source control platform.

    2. Click the button **Confirm**, after creating the repositories, for FortiSOAR to check if the specified repositories exist.

7. Click the button **Push** to push the content from FortiSOAR to the specified branch of the repository mentioned in Production Content.

    Pushing overwrites the contents of the repository mentioned in Production Content.

    You can click the button **Skip** to push the contents later.

8. Click the button **Finish** to finish setting up the production environment.

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
