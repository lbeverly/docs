---
title: SSHing to a Server
menu:
  main:
    parent: 'setup'
    weight: 8
aliases:
  - /docs/ssh
---

Once the [initial configuration]({{% relref "initial-configuration.md" %}}) is
complete, ScaleFT Users can SSH to all enrolled servers.

## Using sft client

From an enrolled client, run `sft ssh <hostname>` where `<hostname>` is
the name of any enrolled host. You can see a list of available hosts by
browsing to your project in the ScaleFT Dashboard.

### `sft ssh`

{{% terminal %}}
<div>[alice@mylaptop]$ sft ssh web0.example.com
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
----------------------------------------------------------------
  Ubuntu 15.04                                built 2016-01-06
----------------------------------------------------------------
Last login: Thu Jan 4 07:14:03 2016 from 198.51.100.23
alice@web0$</div>{{% /terminal %}}

**Note:** the first time you run `sft ssh` you will be prompted to approve your
client's access to infrastructure credentials. This approval will last for up to
10 hours.

<img alt="client authorization screenshot" src="/docs/static/client-request-authorization.png" style="max-height: 621px;" />



### Using sft as a ProxyCommand for ssh

**Note:** With the auto-generated configuration, you will not be prompted to
approve your client's access automatically when you run `ssh`. If your client
is authorized, you will be connected automatically, otherwise you will see a
warning indicating that your client needs to be re-authorized. You can change
this behavior by omitting the "-q" flag. However, doing so will result in
you being prompted to authorize sft any time you use ssh, even for hosts not
currently managed by ScaleFT.

{{% terminal %}}
<div>[alice@mylaptop]$ sft proxycommand --config
# Add this to your $HOME/.ssh/config
Match exec "/Users/user/go/bin/sft resolve -q %h"
    ProxyCommand "/Users/user/go/bin/sft" proxycommand %h
    UserKnownHostsFile "/Users/user/Library/Application Support/ScaleFT/proxycommand_known_hosts"

[alice@mylaptop]$ sft proxycommand --config >> ~/.ssh/config
[alice@mylaptop]$ ssh web0.example.com
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
----------------------------------------------------------------
  Ubuntu 15.04                                built 2016-01-06
----------------------------------------------------------------
Last login: Thu Jan 4 07:14:03 2016 from 198.51.100.23
alice@web0$</div>{{% /terminal %}}

### Using sft with "Bastion" hosts

In many environments, you cannot reach hosts directly, but instead must
traverse through a "bastion" or "gateway" host. With ScaleFT this is easy, and secure.

ScaleFT uses established best-practice for traversing bastion-hosts securely,
and does this for you transparently. Your connection to the target host will be
encrypted from your client all the way to the remote target, without any
intermediate host being able to snoop on you. This is the same method of
bastion traversal achieved by using chained "ProxyCommand" configurations with
openssh's client "ProxyCommand" option.

You can specify bastions with the `--via` command line option to `sft ssh`, and
`sft proxycommand`.

{{% terminal %}}
<div>[alice@mylaptop]$ sft ssh --via bastion.example.com web0.example.com
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
----------------------------------------------------------------
  Ubuntu 15.04                                built 2016-01-06
----------------------------------------------------------------
Last login: Thu Jan 4 07:14:03 2016 from 198.51.100.23
alice@web0$</div>{{% /terminal %}}

This can be made even easier, if you have servers that you always traverse a
bastion to reach, you can add that bastion to the [server's configuration]({{% relref "docs/sftd.md" %}})

When a Bastion is specified in a server's configuration, e.g.

```Bastion: bastion.example.com```

sft clients need not do anything else to connect securely to that server. Given
the same web0.example.com as above that requires you connect through a bastion,
a client connection looks like the following:

{{% terminal %}}
<div>[alice@mylaptop]$ sft ssh web0.example.com
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
----------------------------------------------------------------
  Ubuntu 15.04                                built 2016-01-06
----------------------------------------------------------------
Last login: Thu Jan 4 07:14:03 2016 from 198.51.100.23
alice@web0$</div>{{% /terminal %}}

And this works when using `sft proxycommand` too

{{% terminal %}}
<div>[alice@mylaptop]$ ssh web0.example.com
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-15-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
----------------------------------------------------------------
  Ubuntu 15.04                                built 2016-01-06
----------------------------------------------------------------
Last login: Thu Jan 4 07:14:03 2016 from 198.51.100.23
alice@web0$</div>{{% /terminal %}}
