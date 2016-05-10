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
added to the Project for an **`sftd`**-managed server, **`sftd`** will modify the sudoers file to
include those Users.

***
## Installation

Add [ScaleFT to your package manager](/docs/linux-package-manager). Then run `sudo apt-get install scaleft-server-tools` or `sudo yum install scaleft-server-tools`. For detailed instructions specific to your operating system, see:

- [Installing sftd on CoreOS]({{% relref "sftd-coreos.md" %}})
- [Installing sftd on Redhat, CentOS, & Fedora]({{% relref "sftd-redhat.md" %}})
- [Installing sftd on Ubuntu & Debian]({{% relref "sftd-ubuntu.md" %}})
- [Installing sftd on Windows]({{% relref "sftd-windows.md" %}})

***
## Files and Paths

### Linux and Unix-like operating systems

`sftd` on Linux runs under the `root` user.  Paths follow the Linux Standard Base specifications when applicable. 

#### State Directory

**`/var/lib/sftd`**

#### Config File

**`/etc/sft/sftd.yaml`**

#### Log Directory:

**`sftd`** uses the system logger when available.

#### Enrollment Token:

**`/var/lib/sftd/enrollment.token`**

****

### Windows Server

**`sftd`** on Windows runs under the **`LocalSystem`** account. **`%LOCALAPPDIR%`** is the default prefix for all filesystem paths.

#### State Directory:

**`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT`**

#### Config File:

**`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\sftd.yaml`**

#### Log Directory:

**`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\Logs`**

#### Enrollment Token:

**`C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token`**

***
## Configuration File

**`sftd`** reads **`sftd.yaml`** in order to set configuration settings.  This file is in the [YAML](http://yaml.org/) format.

If this file is not available, **`sftd`** proceeds with the default values.

### Default Configuration:

```yaml
---
# Common Configuration Options:
#
# AccessAddress is unset by default
AutoEnroll:            true
# Bastion is unset by default 
# CanonicalName is unset by default
# InitialURL is unset by default
```
***
### Common Configuration Options
#### **`AccessAddress`** 
_default: unset_ 

For hosts with multiple interfaces, or behind DNATs; specifies the
address clients will use when connecting to this host. 

#### **`AutoEnroll`**
 _default: `true`_

`true` or `false`. When true, **`sftd`** will attempt to automatically enroll
with ScaleFT on initial startup.

#### **`Bastion`**
_default: unset_

Specifies the bastion-host clients will automatically use when connecting to
this host.  
*(see: [SSHing to a server]({{% relref "ssh.md" %}}) for more details)*

#### **`CanonicalName`**
_default: unset_

Specifies the name clients should use/see when connecting to this host.
Overrides the name found with `hostname`

#### **`InitialURL`**
_default: unset_

When AutoEnroll is set to true, this option specifies the InitialURL that the
server can use to auto-enroll.  When an enrollment.token is provided, this
option is ignored. 

***
### Additional Configuration Options

#### **`BufferFile`**
_default: `/var/lib/sftd/buffer.db`_

Path-prefix to the file(s) that **`sftd`** will use for it's local buffer store.
Individual buffers will have a '.' and an incrementing number will be appended
to the path-prefix. BufferFiles which have been synchronized will be removed
automatically.

#### **`EnrollmentTokenFile`**
_default: `/var/lib/sftd/enrollment.token`_

Path to the file containing a secret token for token based enrollment. This
file is deleted after a successful enrollment to the platform.


#### **`ServerFile`**
_default: `/var/lib/sftd/device.server`_

Path to the file that sftd uses to store the server URL that it will connect to.

#### **`SSHDConfigFile`**
_default: `/etc/ssh/sshd_config`_

Path to **`sshd`** configuration file. *Note **`sftd`** will modify this file*

#### **`TokenFile`**
_default: `/var/lib/sftd/device.token`_

Path to file that sftd uses to store its secret token for authentication to ScaleFT.

#### **`TrustedUserCAKeysFile`**
_default: `/var/lib/sftd/ssh_ca.pub`_

Path for **`sftd`** to write the list of trusted SSH Certificate authorities to.

***
## Command Line Options

* `--conf`: Provide alternative configuration file path.
* `--debug-device-info`: Prints detected device information to stderr and then exits.
* `-h`, `--help`: Display help.
* `-v`, `--version`: Display version.
* `--syslog`: Force syslog logging.

***
## Environment Variables

**`sftd`** reads the following variables when starting:

  * **`SFT_DEBUG`**:
    Prints additional debugging to **`stderr`** when set.
