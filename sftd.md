---
title: sftd Reference
category: Reference
weight: 5
---

sftd -- ScaleFT Daemon
=============================================

## Synopsis

`sftd` [options...] command...

## Description

**sftd** run on you servers and provides integration with the ScaleFT platform.

For ScaleFT Access it rotates project-level CA Certificates and manages local user accounts.

## Configuration File

`sftd` reads `/etc/sft/sftd.yaml` in order to set configuration settings.  This file is in the [YAML](http://yaml.org/) format.

### Configuration Options

* `AutoEnroll`: `sftd` will attempt to automatically enroll on initial startup to ScaleFT. (default: `true`): 
* `BufferFile`: Base path for `sftd` to write a local buffer for later synchronization to the ScaleFT Platform.  Path is appended to with `.XXXXX` where `XXXXX` is replaced with an incrementing number.  (default: `/var/lib/sftd/buffer.db`)
* `EnrollmentTokenFile`: Path to the file containing a secret token for token based enrollment.  This file is deleted after a successful enrollment to the platform. (default: `/var/lib/sftd/enrollment.token`)
* `InitialURL`: URL to ScaleFT instance to use for initial enrollment.
* `ServerFile`: Path to file containing the ScaleFT server URL. (default: `/var/lib/sftd/device.server`)
* `SSHDConfigFile`: Path to `sshd` configuration file (default: `/etc/ssh/sshd_config`)
* `TokenFile`: Path to file containing the secret token for authentication to ScaleFT. (default: `/var/lib/sftd/device.toke`)
* `TrustedUserCAKeysFile`: Path for `sftd` to write the list of trusted SSH Certificate authorities to. (default: `/var/lib/sftd/ssh_ca.pub`)

### Configuration Example

An example of enrolling a server with a custom ScaleFT instance:
```yaml
AutoEnroll = true
InitialURL = "https://scaleft.example.com"
```

## Command Line Options

* `--conf`: Provide alternative configuration file path.
* `--debug-device-info`: Prints detected device information to stderr and then exits.
* `-h`, `--help`: Display help.
* `-v`, `--version`: Display version.
* `--syslog`: Force syslog logging.

## Environment Variables

`sftd` reads the following variables when starting:

  * `SCALEFT_DEBUG`:
    Prints additional debugging to `stderr` when set.
