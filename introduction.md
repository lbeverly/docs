---
title: "Introduction"
menu:
  main:
    parent: 'user-guide'
    weight: 0
---

## Overview

ScaleFT is cloud-native security platform that provides secure and reliable authentication to Linux servers.

## Components

ScaleFT consists of three components:

1. ScaleFT Platform
2. ScaleFT server daemon
3. ScaleFT client application

## Configuration

In order to use ScaleFT you will need to:

1. Create a Team in the ScaleFT platform, and configure it to work with your identity provider to authenticate members of your team.
2. Create a Project in ScaleFT and grant users access to it.
3. Install the ScaleFT server daemon (`sftd`) on one or more servers, and enroll those servers in a Project.
4. Have team members install the ScaleFT client application and enroll in your Team.

Once you have performed these steps, your servers will be automatically configured to trust certificates issued by the ScaleFT platform as a way of authenticating SSH users.

The client application installed by each of your team members will connect to the ScaleFT platform to authenticate users against your identity provider. While a team member remains authenticated the client will periodically download certificates that can be used to authenticate to any servers that the team member is configured to have access to.

## Short Lived Certificates

ScaleFT uses short lived certificates, signed by a CA managed by the ScaleFT Platform, in order to grant users automatically-expiring access to your Linux servers. Each of these certificates contains information identifying:

1. The ScaleFT project that the certificate was issued for
2. The Linux username of the user the certificate was issued to
3. The time at which the certificate expires

Each certificate is only valid for 5 minutes after it is issued, making it a low value target for attackers. Shortly before a certificate expires the ScaleFT client will contact the ScaleFT platform, and as long as the user remains authenticated and authorized, the client will automatically download a renewed valid for another 5 minutes.
