| [Home](../README.md) |
|----------------------|

## Including Connector Installation and Configuration in Source Control

Connectors and their configuration information can be exported to source control to save time lost in configuration and to keep the sensitive data protected while allowing functionality.

> [!NOTE]
> 1. For this task the connector must be installed and configured on a production or a development environment.
> 2. The source control repos hosting development or production settings must be **Private**.
>    - [Making a repository private - GitHub](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility#making-a-repository-private)
>    - [Change project visibility - GitLab](https://docs.gitlab.com/user/public_access/#change-project-visibility)

1. [Edit](./editing-export-template.md) the export template.

2. Select **Connectors** and click **Continue**.

3. Select **Connectors** from the left pane.

4. Select the checkbox **Only Show Configured Connectors** from the top left to export only configured connectors.

5. Select the checkbox **Export All** to select both *Installation* and *Configuration* of connectors.

6. Click **Save** to save the export settings.

7. [Save](./usage.md#saving-development-settings) the development or production settings to export connectors' installation and configuration to source control.

8. [Apply Latest Content](./usage.md#applying-latest-changes-in-production-environment) to install connectors and import their configurations in a production environment.

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
