| [Home](../README.md) |
|----------------------|

# Upgrade Instructions

This section points out some actions to take before and after the upgrade to **Continuous Delivery** `v3.0.0`.

> **IMPORTANT**: Follow these instructions closely and do not skip.

## Prerequisites

- Update the **GitHub** connector to `v1.2.0` before initiating upgrade. Install if required.
- Update the **GitLab** connector to `v2.0.0` before initiating upgrade. Install if required.

## Before upgrade

 1. **Take Backup**: Export the existing templates ().
 
 2. **Upgrade**: Upgrade the **Continuous Delivery** solution pack to `v3.0.0`.
 
 3. **Delete**: Delete the following newly-added export templates if they have no **Last Export Date**.
    - Source Control - Production Content
    - Source Control - Development Settings
    - Source Control - Production Settings
 
 4. **Restore From Backup**: Import the templates again using the import wizard (restore from backup).

## After Upgrade

Perform these actions after a successful upgrade to **Continuous Delivery** `v3.0.0`.

1. Take backup of **02 - Use Case - CICD** playbook collection.

2. Delete the following playbooks:
    - GitHub - Update Remote Repository
    - GitHub - Update Issue
    - GitHub - Push Changes
    - GitHub - Merge Pull Request
    - GitHub - List Repository Issue
    - GitHub - List Repository Collaborator
    - GitHub - List Pull Request
    - GitHub - List Pull Request Reviews
    - GitHub - Fetch Release
    - GitHub - Delete Branch
    - GitHub - Create or Update File Content
    - GitHub - Create Repository
    - GitHub - Create Release
    - GitHub - Create Pull Request
    - GitHub - Create Issue
    - GitHub - Create Issue Comment
    - GitHub - Create Branch
    - GitHub - Clone Repository
    - GitHub - Add Reviewers for a Pull Request
    - GitHub - Add Repository Collaborator
    - GitHub - Add Pull Request Review
    - Get FortiSOAR Export Templates

3. Run the **Continuous Delivery** configuration wizard again. Refer to the section [Configuration Wizard](./setup.md#setup-continuous-delivery-on-fortisoar).

4. Click **FortiSOAR Settings** > **Export Wizard**. Uncheck the **Attachments** module from the following export templates:
    - Source Control - Production Content
    - Source Control - Production Settings
    - Source Control - Development Settings

5.  Perform following steps to rename the operation **Map GitHub Username** to **Map Source Control Username**:
    - **Production Environment**
        1. Navigate to the module **Continuous Delivery**.
        2. Click **Production** tab > **Map Source Control Username** card.
        3. Rename the title to **Map Source Control Username**.
    
    - **Development Environment**
        1. Navigate to **Continuous Delivery** > **Development** tab
        2. Click **Map Source Control Username** card
        3. Rename the title to **Map Source Control Username**. 

6. Map the application administrator and developer users in FortiSOAR with their respective source control usernames, again. Run the operation **Map Source Control Username** from *Production* and *Development* environments.