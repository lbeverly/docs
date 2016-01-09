---
title: Server Daemon - sftd
menu:
  main:
    parent: 'reference'
---

## Synopsis

`sftd` [options...] command...

## Description

**sftd** is a deamon that runs on your servers and provides integration with ScaleFT. For ScaleFT Access it installs trusted CA certificates, tracks logins to the server, and manages local user accounts.

## Installation

Add [ScaleFT to your package manager](/docs/linux-package-manager). Then run:

```sudo apt-get install scaleft-server-tools```

or

```sudo yum install scaleft-server-tools```

## Configuration File

`sftd` reads `/etc/sft/sftd.yaml` in order to set configuration settings.  This file is in the [YAML](http://yaml.org/) format.  If this file is not available, `sftd` proceeds with the default values.

### Configuration Options

| Option        | Default Value | Description  |
|:------------- | ------------- |:-------------|
| `AutoEnroll` | `true` | `sftd` will attempt to automatically enroll on initial startup to ScaleFT. |
| `BufferFile` | `/var/lib/sftd/buffer.db` | Base path for `sftd` to write a local buffer for later synchronization to the ScaleFT platform.  Path is appended to with `.` and an incrementing number as the program synchronizes to the ScaleFT platform. |
| `EnrollmentTokenFile` | `/var/lib/sftd/enrollment.token` | Path to the file containing a secret token for token based enrollment.  This file is deleted after a successful enrollment to the platform.
| `InitialURL` | | URL to ScaleFT instance to use for initial enrollment. |
| `ServerFile` | `/var/lib/sftd/device.server` | Path to file containing the ScaleFT server URL. |
| `SSHDConfigFile` | `/etc/ssh/sshd_config` | Path to `sshd` configuration file |
| `TokenFile` | `/var/lib/sftd/device.token` | Path to file containing the secret token for authentication to ScaleFT. |
| `TrustedUserCAKeysFile` | `/var/lib/sftd/ssh_ca.pub` | Path for `sftd` to write the list of trusted SSH Certificate authorities to. |

### Configuration Example

An example of enrolling a server with a custom ScaleFT instance:
```yaml
AutoEnroll: true
InitialURL: https://scaleft.example.com
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
