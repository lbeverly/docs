---
title: "Getting Started"
menu:
  main:
    parent: 'user-guide'
    weight: 0
---

## Getting Started

To use ScaleFT, you must belong to a team. Once your organization has created a team for you, you can sign into the ScaleFT Dashboard.

## Installing the client app

### OSX

Download the app [here](https://dist.scaleft.com/client-tools/mac/latest/ScaleFT.pkg).

This will install the `sft` binary to `/Applications/ScaleFT.app/Contents/MacOS/sft` -- you may wish to symlink this into your $PATH:

    sudo ln -s /Applications/ScaleFT.app/Contents/MacOS/sft /usr/local/bin/

### Linux

First, [add ScaleFT to your package manager](linux-package-manager.html).

To install the sft binary, run:

```sudo apt-get install scaleft-client-tools``` or

```sudo yum install scaleft-client-tools```

To use scaleft URLs with ScaleFT Access, install the handler with:

```sudo apt-get install scaleft-url-handler``` or

```sudo yum install scaleft-url-handler```


## Enrolling your workstation into your team

Enrolling your workstation means using your ScaleFT web credentials to assert that the workstation you enroll is authorized to receive credentials for you.

Enroll your workstation with ScaleFT by running `sft enroll`. This should open the ScaleFT Dashboard and prompt you to enroll your workstation:

    /Applications/ScaleFT.app/Contents/MacOS/sft enroll --default

### Manual CLI

Log into your AWS instance by running `sft ssh <aws-instance-id>`

When you run `sft ssh`, the client:

1. Runs you through a login flow and receives an auth token, which grants your
   workstation permission to issue production credentials for 10 hours. This
   number will be adjustable. The client will re-use this token until it
   expires.
2. Searches for a server in ScaleFT matching the ID you specified. Today this
   must be an AWS instance ID or hostname, but in the future we will support:
   1. ScaleFT server IDs
   2. IP addresses
   3. Other cloud-provider specific identifies
   4. And more
3. Requests credentials for the specified server from ScaleFT. ScaleFT returns
   a signed SSH key pair, the IP address to connect to and the user name to
   use.
4. Executes `ssh` with the credentials and connection information returned from
   ScaleFT.

If you run `sft ssh` a second time within a 10 hour period you won't need to
log in again.
