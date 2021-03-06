---
edit_link: ''
title: Build Using the XDS Dashboard
origin_url: >-
  https://git.automotivelinux.org/src/xds/xds-docs/plain/docs/part-1/create-app-build-dashboard.md?h=halibut
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/devguides/halibut/xds-docs-guides-devguides-book.yml -->

# Build Using the XDS Dashboard

One option for building your application using XDS is to use
the XDS Dashboard.
Building the application consists of using the dashboard
to declare your project and then initiate the build.

## Declare Project

Follow these steps to declare the project:

1. Open a Web Browser and connect to to the XDS Dashboard.

   The URL you use depends of your configuration (e.g. `http://localhost:8800`).

2. Open the right sidebar and select the `Projects` entry to open the
   project page.
   Once the page is open, declare a new project by clicking on the
   "plus" icon next to "Add Project":

   ![](./pictures/xds-dashboard-icon-2.png){:: style="margin:auto; display:flex"}

   When you declare the project, XDS creates the `xds-project.conf`
   configuration file if one does not already exist.
   You should examine this configuration file before you build the
   project to be sure all configurations are correct for your project.

   The configuration file can be very useful when you plan to use
   XDS client tools such as `xds-cli` or `xds-gdb`.

   <!-- pagebreak -->

3. Set `Sharing Type` appropriately depending on your Client Part
   configuration:

   ![](./pictures/xds-dashboard-prj-1.png){:: style="width:90%; max-width:560px; margin:auto; display:flex"}

   <!-- section-note -->
   **NOTES:**

   - When `Path mapping` type is selected, you must clone your project into
     `$HOME/xds-workspace` directory, which is named **Local Path** in the modal window.

   - If XDS server is running in the XDS docker container
     the **Server Path** must be set to `/home/devel/xds-workspace/<xxx>`
     where `<xxx>` is your project directory name.
     See the "[Installation based on Docker container](server-part.html#docker-container))"
     section for more information.

   - If you select `Cloud Sync`, you can clone your project wherever you want on
     your local disk.
   <!-- end-section-note -->

## Build the Application

Building the application requires opening the build page's "build entry" in the
left navigational pane, selecting both the project and the SDK, and
then initiating the build.

<!-- section-note -->
**NOTE:**

To use the `helloworld-native-application` example, you need to provide
some configuration items.
Specifically, you must pass values for both the
`RSYNC_TARGET` and `RSYNC_PREFIX` environment variables.
To pass these variables, use the `Settings` window in the `Build` tab.
You can use the `Env variables` field to pass a list of environment variables
that are set on the server prior to the build occurring.
You must separate individual variables using the semi-colon character:

```
RSYNC_TARGET=root@<mytarget>;RSYNC_PREFIX=/opt
```

When you pass these variables, substitute `<mytarget>` with the valid
target IP address or DNS name entry.
<!-- end-section-note -->

Follow these steps to build the application:

1. Open the build page build entry in the left-hand navigation pane:

   ![](./pictures/xds-dashboard-icon-3.png){:: style="display:inline; padding:0;"},

2. Select your **Project**.

3. Seclect the **Cross SDK** you want to use.

4. Click the **Clean / Pre-Build / Build / Populate** buttons to execute
   the build action you want.

   ![](./pictures/xds-dashboard-prj-2.png){:: style="width:90%; max-width:600px; margin:auto; display:flex"}
