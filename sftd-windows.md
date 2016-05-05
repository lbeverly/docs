---
title: "Windows Server"
menu:
  main:
    parent: 'server'
    name: "Windows Server"
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

Download the ScaleFT Server Tools [here](https://dist.scaleft.com/server-tools/windows/v0.18.6/ScaleFT-Server-Tools-0.18.6.msi).

The MSI can either be installed manually, or via msiexec:

```
msiexec.exe /qb /I ScaleFT-Server-Tools-0.18.6.msi
```

## PowerShell script for automatic installation on Cloud Instances

ScaleFT Server Tools can be automatically installed on AWS and other cloud enviroments using the following userdata script. 
If you are using an enrollment token be sure to replace the value of `$enrollment_token`. If you have associated your 
AWS account with your ScaleFT project, you can omit the first half of the script which is responsible for 
writing the enrollment token.

```ps1
<powershell>
# Write the Enrollment Token
$enrollment_token = "ENROLLMENT TOKEN GOES HERE"
$enrollment_token_path = "C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token"
New-Item -ItemType directory -Path (Split-Path $enrollment_token_path -Parent)
$enrollment_token | Out-File $enrollment_token_path -Encoding "ASCII"

# Install ScaleFT Server Tools
$installer_url = "https://dist.scaleft.com/server-tools/windows/v0.18.6/ScaleFT-Server-Tools-0.18.6.msi"
$installer_path = [System.IO.Path]::ChangeExtension([System.IO.Path]::GetTempFileName(), ".msi")
(New-Object System.Net.WebClient).DownloadFile($installer_url, $installer_path)
msiexec.exe /qb /I $installer_path
</powershell>
```

