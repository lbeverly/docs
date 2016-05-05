---
title: Setting up a Client
menu:
  main:
    parent: 'setup'
    weight: 7
aliases:
  - /docs/enrolling-a-client
---

ScaleFT credentials are scoped to the combination of a User and the User's device.
Users must first install the ScaleFT Client, and then enroll their devices, similarly
to how servers enroll in Projects. Verifying the details of the devices that Users use
to access your infrastructure allows ScaleFT to make better-informed decisions about the
risk of issuing credentials.

- [Installing the ScaleFT Client on Mac OS X]({{% relref "docs/sft-osx.md" %}})
- [Installing the ScaleFT Client on Redhat, CentOS, & Fedora]({{% relref "docs/sft-redhat.md" %}})
- [Installing the ScaleFT Client on Ubuntu]({{% relref "docs/sft-ubuntu.md" %}})


## Enrolling Your Device

Once the ScaleFT Client is installed, the User should enroll the device. To
do so, run `sft enroll` in your terminal.

{{% terminal %}}<div>ggreer@carbon:~% sft enroll
Waiting on browser...




</div>{{% /terminal %}}

This should open a web browser, allowing you to choose your Team and complete the client enrollment process.

<img src="/docs/static/client-enrollment-approval.png" style="max-height: 621px;" />

After the client is approved, `sft` will report success:

{{% terminal %}}<div>ggreer@carbon:~% sft enroll
Waiting on browser...
Browser enrollment completed successfully.
Enrolled Device: user=ggreer team=example
ggreer@carbon:~%


</div>{{% /terminal %}}

At this point, you can [ssh to your enrolled servers]({{% relref "ssh.md" %}}).
