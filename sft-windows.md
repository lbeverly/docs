---
title: "ScaleFT Client on Windows"
menu:
  main:
    parent: 'client'
    name: "Windows Client"
    weight: 5
---

## Installation

Download the ScaleFT client [here](https://dist.scaleft.com/client-tools/windows/latest/ScaleFT.msi).

Run the installation MSI.

<img src="/docs/static/sft-windows-installation-complete.png" style="max-height: 385px;" />

After installing, be sure to [enroll your client]({{% relref "enrolling-a-client.md" %}}).


## Usage

Once your client is enrolled, you can `ssh` to your servers with `sft ssh [hostname]`. For more details, see [SSHing to a Server]({{% relref "ssh.md" %}}).
Logs can be found in `C:\Users\<USERNAME>\AppData\Local\ScaleFT\Logs`.


## Uninstalling

To uninstall the ScaleFT client:

- Remove the ScaleFT application using the [Apps & features](http://windows.microsoft.com/en-us/windows-10/repair-or-remove-programs#v1h=tab01) control panel.
