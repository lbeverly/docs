---
title: Setting up a Client
menu:
  main:
    parent: 'setup'
    weight: 7
aliases:
  - /docs/enrolling-a-client
---

Users must first install the ScaleFT Client, and then register their workstations with ScaleFT.

<img src="/docs/static/basic-usage-images/User-Setup@1x.png" style="max-width: 581px;" class="center-block" />

- [Installing the ScaleFT Client on Mac OS X]({{% relref "docs/sft-osx.md" %}})
- [Installing the ScaleFT Client on Redhat, CentOS, & Fedora]({{% relref "docs/sft-redhat.md" %}})
- [Installing the ScaleFT Client on Ubuntu]({{% relref "docs/sft-ubuntu.md" %}})
- [Installing the ScaleFT Client on Windows]({{% relref "docs/sft-windows.md" %}})

## Enrolling Your Workstation

Once the ScaleFT Client is installed, the User should enroll their workstation.

To do so, run `sft enroll` in your terminal.

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

At this point, you can [ssh to your enrolled servers]({{% relref "ssh.md" %}}) using Client Certificate Authentication.
