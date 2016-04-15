---
title: Windows (Beta)
menu:
  main:
    parent: 'none'
    weight: -50
---

## Overview

Using ScaleFT with Windows requires installing the ScaleFT Server Tools on the server, and Client Tools on the client.
See below for directions.

Once the ScaleFT Server Tools are installed on the server and the server enrolled, the ScaleFT Agent (`sftd`) does two
things:

1. Creates local accounts for all ScaleFT users who should have access to the server, very similar to on Linux.
2. Runs an additional Access Broker which listens on port 4421.

The Access Broker uses TLS 1.2 to authenticate all clients using client certificates that can only be issued by the
ScaleFT platform. The Broker process runs at the "Low" integrity level.

#### Connection Establishment

In order to establish an RDP connection, the ScaleFT client:

1. Communicates with ScaleFT platform to get short-lived credentials it can use to authenticate to the Access Broker.
2. Optionally establishes an SSH tunnel through any intermediate bastion servers. If any bastion also uses ScaleFT
   for authentication, short-lived credentials are fetched transparently.
3. Connects to the ScaleFT broker (over the SSH tunnels, if applicable) and authenticates using the short-lived
   certificate provided by the platform. The client also authenticates the server's host certificate against one
   provided by the platform to defend against man-in-the-middle attacks.
4. Negotiates a proxied RDP connection via the Broker. The client is then able to start a TCP server on a random port
   on the client, which is proxied through the broker to the RDP service on the server.
5. The client writes an RDP connection file containing the connection info, including the random local port on which
   the client is now listening. It then opens the Windows Terminal Services client with this configuration.

The RDP Client connects to the local TCP port and is forwarded to the RDP service on the server. The RDP server is able
to automatically authenticate as the user without any further prompting.

## Configuration

### Server Configuration

Server configuration follows the same [principles](/docs/enrolling-a-server/) as it does on Linux.

In order to enroll the server using an enrollment token, write the token to:

```
C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token
```

Alternatively if you are using AWS you can [associate your AWS account with a ScaleFT
Project](/docs/enrolling-a-server/#associating-an-aws-account-with-a-scaleft-project).

ScaleFT Server Tools installers are available [here](https://dist.scaleft.com/server-tools/windows/).

ScaleFT Server Tools can be automatically installed on AWS using the following userdata script. If you are using an
enrollment token be sure to replace the value of `$enrollment_token`. If you have associated your AWS account with your
ScaleFT project, you can omit the first half of the script which is responsible for writing the enrollment token.

```ps1
<powershell>
# Write the Enrollment Token
$enrollment_token = "ENROLLMENT TOKEN GOES HERE"
$enrollment_token_path = "C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token"
New-Item -ItemType directory -Path (Split-Path $enrollment_token_path -Parent)
$enrollment_token | Out-File $enrollment_token_path -Encoding "ASCII"

# Install ScaleFT Server Tools
$installer_url = "https://dist.scaleft.com/server-tools/windows/v0.18.0/ScaleFT-Server-Tools-0.18.0.msi"
$installer_path = [System.IO.Path]::ChangeExtension([System.IO.Path]::GetTempFileName(), ".msi")
(New-Object System.Net.WebClient).DownloadFile($installer_url, $installer_path)
msiexec.exe /qb /I $installer_path
</powershell>
```

### Client Configuration

Connecting to a Windows server requires a Windows client running ScaleFT Client v0.18.0 or above. Client Tools
installers are available [here](https://dist.scaleft.com/client-tools/windows/).

Once the client is installed it must be enrolled by running `sft enroll`.

### Connecting to a Server

To RDP to a server using ScaleFT run:

```
sft rdp <server-name>
```

If you need to traverse one or more bastions use `--via` arguments, such as:

```
sft rdp --via <first.bastion> --via <second.bastion> <server>
```

## Advanced Server Configuration

### Paths

##### State Directory

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT`

##### Config File

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\sftd.yaml`

##### Log Directory

`C:\Windows\System32\config\systemprofile\AppData\Local\ScaleFT\Logs`

##### Enrollment Token

`C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token`

### Configuration

The configuration format used by `sftd` is the same on Windows as it is on Linux. See the [sftd reference](/docs/sftd/)
for details.