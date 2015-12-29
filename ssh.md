---
title: SSHing to a Server
menu:
  main:
    parent: 'user-guide'
    weight: 5
---

Now that ScaleFT understands your infrastructure, you're ready to SSH to the
server you enrolled.

From the client you previously enrolled run `sft ssh <hostname>` where
`<hostname>` is the name of any enrolled host. You can see a list of available
hosts by browsing to your project in the ScaleFT web interface.

**Note:** the first time you run `sft ssh` you will be prompted to approve your
client's access to infrastructure credentials. This approval will last for ten
hours.
