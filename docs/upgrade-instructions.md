| [Home](../README.md) |
|----------------------|

# Upgrade instructions

This section points out some actions to take before and after the upgrade to **Continuous Delivery** `v3.2.0`.

## Before upgrade

Perform these actions before you start the upgrade.

1. **Take a backup**: Export the existing templates.

2. **Upgrade**: Upgrade the **Continuous Delivery** solution pack to `v3.2.0`.

3. **Delete**: Delete the following newly-added export templates if they have no **Last Export Date**.
    - Source Control - Production Content
    - Source Control - Development Settings
    - Source Control - Production Settings

4. **Restore from backup**: Import the templates again using the import wizard (restore from backup).

## After upgrade

Perform these actions after a successful upgrade to **Continuous Delivery** `v3.2.0`.

1. Run the **Continuous Delivery** configuration wizard again. Refer to the section [Configuration Wizard](./setup.md#setting-up-continuous-delivery-on-fortisoar).

2. Click **FortiSOAR Settings** > **Export Wizard**. Uncheck the **Attachments** module from the following export templates:
    - Source Control - Production Content
    - Source Control - Production Settings
    - Source Control - Development Settings

# Next steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|---------------------|---------------------------|
