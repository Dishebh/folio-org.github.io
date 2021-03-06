---
layout: page
title: Install a new back-end module to reference environments
permalink: /guides/install-backend-module/
menuInclude: no
menuTopTitle: Guides
---

## Introduction

When the initial development of a new back-end (server-side) module is established, and snapshot artifacts are being generated by the continuous integration, then it is able to be added to the folio-ansible configuration, and make it available in the folio-snapshot and folio-testing [reference environments](/guides/automation/#reference-environments).

There is a separate procedure to [install a new front-end module](/guides/install-frontend-module/).

(After the new module has been operating in snapshot and testing environments, and an initial release is ready to be made, then instead follow the [release procedures](/guidelines/release-procedures/#add-to-platforms).)

## Verify MD and required interfaces

First ensure that this new module's [ModuleDescriptor](/guides/module-descriptor/) is deployed and that any required interfaces are available.

For example, consider the `mod-notes` module.
Obtain its MD from the registry and extract the "requires" section:

```
curl -s -S -w'\n' \
  'http://folio-registry.aws.indexdata.com/_/proxy/modules?filter=mod-notes&latest=1&full=true' \
  | jq '.[].requires'
```

That shows that it requires various interfaces, including `users 15.0`

Now ensure that each interface is available, e.g.:

```
curl -s -S -w'\n' \
  'https://folio-snapshot-okapi.aws.indexdata.com/_/proxy/tenants/diku/modules?latest=1&provide=users%3D15.0'
```

If there is a non-empty result for each of the required interfaces, then ready to proceed.
If not, then investigate further and consult the relevant back-end module developers.

## Ensure LaunchDescriptor

Ensure that this new module's [ModuleDescriptor](/guides/module-descriptor/) includes the Docker-based [LaunchDescriptor](/guides/module-descriptor/#launchdescriptor-properties).

Its properties will specify the memory allocation, whether this module utilises a database, and can document other environment variables, etc.

## Ensure local Docker

Ensure that the module will operate with a local Vagrant VM.

Follow the guide to verify [Local module as Docker container](/guides/run-local-folio/#local-module-as-docker-container).

## Declare new module

Prepare the Jira ticket to guide the process, and request that the new back-end module be enabled for the snapshot and testing. Specify "Development Team: FOLIO DevOps" to be prioritized and scheduled.

The DevOps team will configure the module and conduct various configuration tests.

## Verify deployment

After merge, await the scheduled build of the folio-snapshot and folio-testing [reference environments](/guides/automation/#reference-environments).

Visit the [Software versions](https://folio-snapshot.aws.indexdata.com/settings/about) page of each to verify that the new module is present.

<div class="folio-spacer-content"></div>

