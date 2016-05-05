---
title: Server Daemon - sftd
menu:
  main:
    parent: 'reference'
    weight: 3
---

## Synopsis

    sftd [options...] command...

## Description

**sftd** is a daemon that runs on your servers and integrates with the ScaleFT Platform.

For ScaleFT Access it installs trusted CA certificates to `sshd`, tracks logins to the server,
and manages local user accounts. If a User Group that has the `server_admin` flag enabled is
added to the Project for an `sftd`-managed server, `sftd` will modify the sudoers file to
include those Users.

## Installation

Add [ScaleFT to your package manager](/docs/linux-package-manager). Then run `sudo apt-get install scaleft-server-tools` or `sudo yum install scaleft-server-tools`. For detailed instructions specific to your operating system, see:

- [Installing sftd on CoreOS]({{% relref "sftd-coreos.md" %}})
- [Installing sftd on Redhat, CentOS, & Fedora]({{% relref "sftd-redhat.md" %}})
- [Installing sftd on Ubuntu & Debian]({{% relref "sftd-ubuntu.md" %}})

## Files and Paths

### Linux and Unix-like operating systems

`sftd` on Linux runs under the `root` user.  Paths follow the Linux Standard Base specifications when applicable. 

##### State Directory

`/var/lib/sftd`

##### Config File

`/etc/sft/sftd.yaml`

##### Log Directory

`sftd` uses the system logger when available.

##### Enrollment Token

`/var/lib/sftd/enrollment.token`

### Windows Server

`sftd` on Windows runs under the `LocalSystem` account. `%LOCALAPPDIR%` is the default prefix for all filesystem paths.

##### State Directory

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT`

##### Config File

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\sftd.yaml`

##### Log Directory

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\Logs`

##### Enrollment Token

`C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token`


## Configuration File

`sftd` reads `sftd.yaml` in order to set configuration settings.  This file is in the [YAML](http://yaml.org/) format.

If this file is not available, `sftd` proceeds with the default values.

### Configuration Options

| Option        | Default Value | Description  |
|:------------- | ------------- |:-------------|
| `AutoEnroll` | `true` | `sftd` will attempt to automatically enroll on initial startup to ScaleFT. |
| `CanonicalName` |  | Specifies the name clients should use/see when connecting to this host. Overrides the name found with `hostname` |
| `Bastion` |  | Specifies the bastion-host clients will automatically use when connecting to this host. |
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

  * `SFT_DEBUG`:
    Prints additional debugging to `stderr` when set.
