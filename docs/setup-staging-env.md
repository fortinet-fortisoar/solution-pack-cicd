| [Home](../README.md) |
|----------------------|

## Setting up the staging environment

A staging environment is a sandbox for testing content developed by content developers before it is rolled out to production. It is optional: set one up only if you want an extra validation layer between development and production.

1. [Set up the production environment](./setup-prod-env.md) on a separate FortiSOAR instance and consider it a *Staging Environment*.

2. [Apply latest changes](./usage.md#applying-latest-changes-in-production-environment) to make the staging instance a clone of the *Production* instance.

The staging environment acts as a production environment for changes that have been successfully tested in the development environment. After ensuring that the content changes are stable in development, [apply latest changes in the production environment](./usage.md#applying-latest-changes-in-production-environment).

# Next steps
 
| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|
