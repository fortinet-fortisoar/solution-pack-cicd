| [Home](./README.md) |
|----------------------|

# What's New

- GitLab is now supported as one of the source control platforms. Earlier, source control was only available for GitHub.

- A new **Pluggable Source Control** framework now connects with any of the available source control platforms.

## Widget Enhancements

Introduced following new widgets:

- **Playbook Execution Wizard** displays continuous delivery solution pack's playbook execution progress on the user interface. This widget can be configured to display execution of any of the playbooks.

- **Playbook Buttons** executes following continuous delivery operations on the widget **Playbook Execution Wizard**:

    - Setup the Source Control for Production Environment

    - Setup the Development Environment

    - Apply Latest Content

    - Save Production Settings

    - Map Source Control Username

    This widget can be configured to place button within any record's detail helping trigger playbooks at the click of a button.

- **JSON to Grid** widget now has following capabilities:

    - Execute grid operations of **Production** or **Development** environment on **Playbook Execution Wizard** widget 

    - Show grid columns even if there is no change request record present  

    - Supported auto refresh of the Grid on create of the change request record 

- **CICD Configuration Wizard** now offers **GitLab**, along with GitHub, as a source control platform and helps configure the selected source control with *Continuous Delivery* solution pack.

## UI Enhancements

- Refreshed infographic on the **Setup** tab of the *Continuous Delivery* solution pack.

- Refreshed infographic on the Continuous Delivery configuration wizard.

## Other Enhancements

- **Map GitHub Username** operation is now **Map Source Control Username**.

- **GitHub** as a term in the *Continuous Delivery* solution pack is now referred to **Source Control** to include current (GitLab and GitHub) and future source control integrations.

- The **Export/Import** workflow operations is now optimized.

- **Closed Issues** records are now viewable in a separate grid under **Apply Latest Changes** in *Development* and *Production* tabs of *Continuous Delivery*.

- Moved all **GitHub** playbooks to the GitHub connector

- Added **Source Control Username** field in the **People** module