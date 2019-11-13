# Installing Cloud Functions Plugin

This section will take you step-by-step through the [setup of the IBM Cloud Functions CLI plugin](https://cloud.ibm.com/functions/learn/cli).

## Install IBM Cloud Functions CLI plugin

Use this command to install the Cloud Functions plugin for the IBM Cloud CLI.

```bash
$ ibmcloud plugin install cloud-functions
```

```bash
Looking up 'cloud-functions' from repository 'IBM Cloud'...
Plug-in 'cloud-functions 1.0.xx' found in repository 'IBM Cloud'
Attempting to download the binary file...
 12.93 MiB / 12.93 MiB [===========================================] 100.00% 1s
13563264 bytes downloaded
Installing binary...
OK
Plug-in 'cloud-functions 1.0.xx' was successfully installed into /Users/Joesephine/.bluemix/plugins/cloud-functions. Use 'ibmcloud plugin show cloud-functions' to show its details.
```

## Test IBM Cloud Functions From The CLI

Run the following command to invoke a test function from the command-line.

```bash
$ ibmcloud fn action invoke whisk.system/utils/echo -p message hello --result
```

```bash
{
    "message": "hello"
}
```

_If this command executes successfully, you have verified that the IBM Cloud CLI and Cloud Functions plugin have been installed and configured correctly. If this does not work, please contact the workshop organizer to provide assistance!_

## Using aliases for the Cloud Functions plugin

The IBM Cloud Functions plugin is referenced as a sub-command under the IBM Cloud CLI by its name `cloud-functions`, but can also be referenced by the shorter aliases `functions`, `fn` and `wsk`.

_**Note**: This `cloud-functions` CLI plugin provides the_ [_Apache OpenWhisk CLI_](https://github.com/apache/incubator-openwhisk/blob/master/docs/cli.md) _as a sub-command under the IBM Cloud CLI. Platform credentials are provided automatically by the IBM Cloud CLI. THis is why one of the aliases is named `wsk`._

---
🎉 **Congratulations, you've successfully configured the IBM Cloud CLI for Cloud Functions development and executed your first serverless function! Let's start using the platform to create our own serverless applications…** 🎉

---

## Target a Resource Group and Namespace

1. List all available resource groups on your account:
```bash
$ ibmcloud resource groups
```
```bash
Retrieving all resource groups under account Josephine Watson's Account as josephine.watson@gmail.com...
OK
Name      ID                                 Default Group   State
Default   2cdb253b144c4d36ae8f1c125a3ab6d5   true            ACTIVE
```

1. Target the desired resource group. In this case we target the group named `Default`:

```bash
$ ibmcloud target -g Default

Targeted resource group default

API endpoint:      https://cloud.ibm.com
Region:            us-south
User:              josephine.watson@gmail.com
Account:           Josephine Watson's Account (87a302ad58884640a45f959d3da6cc77)
Resource group:    Default
CF API endpoint:   https://api.ng.bluemix.net (API version: 2.142.0)
Org:               josephine.watson@gmail.com
Space:             dev
```

1. List all available namespaces for your resource group:

```bash
$ ibmcloud fn namespace list
name                            type         id                                    description
josephine.watson@gmail.com_dev  CF-based     josephine.watson@gmail.com_dev
```