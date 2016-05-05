---
title: "ScaleFT Client on Mac OS X"
menu:
  main:
    parent: 'client'
    weight: 5
---

## Installation

Download the ScaleFT client [here](https://dist.scaleft.com/client-tools/mac/latest/ScaleFT.pkg).

Run the installation package.

<img src="/docs/static/sft-osx-installation-complete.png" style="max-height: 550px;" />

After installing, be sure to [enroll your client]({{% relref "enrolling-a-client.md" %}}).


## Usage

Once your client is enrolled, you can `ssh` to your servers with `sft ssh [hostname]`. For more details, see [SSHing to a Server]({{% relref "ssh.md" %}}).


## Uninstalling

To uninstall the ScaleFT client:

- Delete the ScaleFT application (`/Applications/ScaleFT.app`)
- Delete the symbolic link to sft: `rm /usr/local/bin/sft`
