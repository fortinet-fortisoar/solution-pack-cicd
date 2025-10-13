| [Home](../README.md) |
|----------------------|

## Exporting Sample Alerts/Incidents from Prod Environment

Exporting alerts from production environment can help organizations,

- Analyze and troubleshoot issues thereby continuously improving their operations
- Test the effectiveness of their alert configurations in a safe, controlled environment
- Reduce the risk of security incidents by training their systems on all possible variations of a threat
- Reduce storage in the source system
- Preserve historical data for future reference.

You can tag alerts to be exported, individually, and use a filter to include those tagged alerts in the export template.

Following steps help export alerts or incidents from a FortiSOAR production environment to a development environment:

1. Log in to FortiSOAR's production instance.

2. Select the alert to be exported.

3. Add a tag `sample`. Repeat this step for all alerts to be exported.

4. [Edit](./editing-export-template.md) the export template.

    1. Select **Module** and click **Continue**.

    2. Click the button **Records** against **Alerts**.

    3. You can add a filter criterion to export only those alerts that are marked with the tag `sample`.

        ![](./res/filter-alerts-export-template.png)

    4. Click the button **Update Query**.

    5. Click the button **Continue** to add these alerts to the development settings to be exported to source control.

    6. Click **Save** to save the export settings.

5. [Save](./usage.md#saving-development-settings) the development or production settings to export alerts to source control.

6. [Apply Latest Content](./usage.md#applying-latest-changes-in-production-environment) to import alerts in development environment. 

# Next Steps 
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
