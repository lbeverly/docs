---
title: "CoreOS"
menu:
  main:
    parent: 'server'
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

First, add the ScaleFT signing key:

```
# Add ScaleFT signing key to rkt
sudo rkt trust --prefix=scaleft.com/sftd
```

{{% terminal %}}
<div>robert_chiniquy@ip-172-31-23-43 ~ $ sudo rkt trust  --prefix=scaleft.com/sftd
pubkey: prefix: "scaleft.com/sftd"
key: "https://scaleft.com/dl/scaleft_aci_key.asc"
gpg key fingerprint is: 9634 D6F5 7077 3D74 E127  4FA0 D8C3 DAA1 B6AC 706E
    Subkey fingerprint: 5EF1 0A27 5E1C 7DA9 7234  8358 D263 E4A5 6194 E2B2
  ScaleFT (aci signing) <security+aci@scaleft.com>
Are you sure you want to trust this key (yes/no)?
yes
Trusting "https://scaleft.com/dl/scaleft_aci_key.asc" for prefix "scaleft.com/sftd" after fingerprint review.
Added key for prefix "scaleft.com/sftd" at "/etc/rkt/trustedkeys/prefix.d/scaleft.com/sftd/9634d6f570773d74e1274fa0d8c3daa1b6ac706e"</div>
{{% /terminal %}}

```
# Optionally, pre-fetch a specific version.
rkt fetch scaleft.com/sftd:0.18.5
```

{{% terminal %}}
<div>robert_chiniquy@ip-172-31-23-43 ~ $ sudo rkt fetch scaleft.com/sftd:0.18.5
image: searching for app image scaleft.com/sftd
image: remote fetching from URL "https://dist.scaleft.com/server-tools/linux/v0.18.5/sftd-0.18.5-linux-amd64.aci"
image: keys already exist for prefix "scaleft.com/sftd", not fetching again
image: downloading signature from https://dist.scaleft.com/server-tools/linux/v0.18.5/sftd-0.18.5-linux-amd64.aci.asc
Downloading signature: [=======================================] 473 B/473 B
Downloading ACI: [=============================================] 4.86 MB/4.86 MB
image: signature verified:
  ScaleFT (aci signing) <security+aci@scaleft.com>
sha512-6ecfc7aca9cb9afa41b69e21c7caef1f
robert_chiniquy@ip-172-31-23-43 ~ $</div>
{{% /terminal %}}

Then, install the `scaleft-server-tools` package:

On CoreOS, `sftd` is distributed as an App Container image (`.aci`) file. It runs under the [rkt container engine](https://coreos.com/rkt/) and is managed by a systemd service file.  An example of deploying the systemd service file is below:

```
# Download example unit file
curl --location --output /etc/systemd/system/sftd.service https://dist.scaleft.com/server-tools/linux/latest/sftd.service
```

{{% terminal %}}
<div>robert_chiniquy@ip-172-31-23-43 ~ $ sudo curl --location --output /etc/systemd/system/sftd.service https://dist.scaleft.com/server-tools/linux/latest/sftd.service
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  1037  100  1037    0     0   8809      0 --:--:-- --:--:-- --:--:--  8809</div>
{{% /terminal %}}

```
# Load unit file into systemd
systemctl daemon-reload
systemctl enable sftd.service
systemctl start sftd.service
```

{{% terminal %}}
<div>robert_chiniquy@ip-172-31-23-43 ~ $ sudo systemctl daemon-reload
robert_chiniquy@ip-172-31-23-43 ~ $ sudo systemctl enable sftd.service
Created symlink from /etc/systemd/system/multi-user.target.wants/sftd.service to /etc/systemd/system/sftd.service.
robert_chiniquy@ip-172-31-23-43 ~ $ sudo systemctl start sftd.service
robert_chiniquy@ip-172-31-23-43 ~ $</div>
{{% /terminal %}}

For usage information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
