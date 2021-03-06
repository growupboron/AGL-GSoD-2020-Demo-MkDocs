---
edit_link: ''
title: CLI Commands
origin_url: >-
  https://git.automotivelinux.org/src/xds/xds-docs/plain/docs/part-2/3_xds-cli/3_commands.md?h=halibut
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/devguides/halibut/xds-docs-guides-devguides-book.yml -->

# Commands

## projects

`projects` (short `prj`) command should be used to managed XDS projects.

This command supports following sub-commands:

```bash
add, a      Add a new project
get         Get a property of a project
list, ls    List existing projects
remove, rm  Remove an existing project
sync        Force synchronization of project sources
```

Here are some usage examples:

```bash
# Create/declare a new project
xds-cli prj add --label "myProjectName" --type pm -p /home/seb/xds-workspace/myProject -sp /home/devel/xds-workspace/myProject

# List projects
xds-cli prj ls

# Delete an existing project
xds-cli prj rm 8e49
```

## sdks

`sdks` (alias `sdk`) command should be used to managed cross SDKs.

This command supports following sub-commands:

```bash
get            Get a property of a SDK
list, ls       List installed SDKs
install, i     Install a SDK
uninstall, rm  UnInstall an existing SDK
abort, a       Abort an install action
```

Here are some usage examples:

```bash
# List existing SDKs
xds-cli sdks ls

# Get SDK info
xds-cli sdks get c64d
```

<!-- section-note -->
**Note:**

Refer to the
"[AGL SDKs](../../part-1/install-sdk.html)"
topic for details about SDK installation.

<!-- end-section-note -->

## exec

`exec` command should be used to exec command through XDS system.

For example you can use this command to build your project in XDS system.

This command supports following sub-commands:

`exec` command options are:

**`--id` option or `XDS_PROJECT_ID` env variable (**mandatory option**)**

project ID you want to build

**`--rpath` (short `-p`) or `XDS_RPATH` env variable**

relative path into project

**`--sdkid` (alias `--sdk`) or `XDS_SDK_ID` env variable (**mandatory option**)**

Cross Sdk ID to use to build project.

Here are some usage examples:

```bash
cd $MY_PROJECT_DIR
mkdir build

# Generate build system using cmake
xds-cli exec --id=4021 --sdkid=c226 -- "cd build && cmake .."

# Build the project
xds-cli exec --id=4021 --sdkid=c226 -- "cd build && make all"
```

In case of `xds-agent` is not running on default url:port (that is `localhost:8800`)

You can specify the url using `--url` option :

```bash
xds-cli --url=http://localhost:8800 exec --id=4021 --sdkid=c226 -- "cd build && make all"
```

## misc

`misc` command allows to execute miscellaneous sub-commands such as:

```bash
version, v   Get version of XDS agent and XDS server
status, sts  Get XDS configuration status (including XDS server connection)
```

Here are some usage examples:

```bash
xds-cli misc version --verbose

xds-cli misc sts
```
