---
title: "Introduction"
menu:
  main:
    parent: 'user-guide'
    weight: 0
---

## Overview

ScaleFT is a cloud-native security platform that brings risk-based, dynamic authentication to cloud infrastructure using short-lived certificates.

## Components

ScaleFT is composed of three components:

1. ScaleFT Platform
2. ScaleFT server daemon
3. ScaleFT client application

## Concepts

### Team

A Team is a group of people who work together on infrastructure and share an authentication method (such as OAuth).

### Project

A Project is a collection of resources (such as servers, load-balancers, web services, or VPNs) that share configurations and associated User Group permissions.

### Group

A Group is a collection of Users and Team permissions. Groups are linked to Projects to describe Users' permissions within that Project.

### User

A User is a member of a Team. Users can belong to multiple Groups and have multiple Clients.

### Client

The ScaleFT Client is installed on a device (such as a laptop or workstation) which a User uses to access infrastructure. The ScaleFT Client manages the dynamic credentials on the device so the User can transparently access ScaleFT-managed infrastructure.

## Initial Configuration

To get started with ScaleFT, once you have an invite code:

1. Create a Team in the ScaleFT platform, and configure it to work with your identity provider to authenticate members of your team.
2. Create a Project in ScaleFT link it to a User Group (you can also use the universal groups `everyone` and `owners`).
3. Install the ScaleFT server daemon (`sftd`) on one or more servers, and enroll those servers in a Project.
4. Have team members install the ScaleFT client application and enroll their Clients in your Team.

Once you have performed these steps, your servers will be automatically configured to trust certificates issued by the ScaleFT platform as a way of authenticating SSH users. You can also configure `sftd` to create user accounts for the members of your Team, and even manage `sudo` access with ScaleFT roles and permissions.

The client application installed by each of your team members will connect to the ScaleFT platform to verify users against your identity provider. While a team member remains authenticated, the client manages the dynamic credentials that enable that User to authenticate to any resources they may access.

## Short Lived Certificates

ScaleFT Projects manage Certificate Authorities to issue short-lived certificates, which are managed transparently on the User's device by the ScaleFT Client.

Each of these certificates contains the following information:

1. The ScaleFT Project for which the certificate was issued
2. The username to be used on the server of the Scaleft User to whom the certificate was issued
3. The time at which the certificate expires

Before a certificate expires, the ScaleFT Client will re-verify that the User should continue to have access, and as long as the user remains authenticated and authorized, the Client will automatically install a renewed certificate valid for a brief period of time.

Since ScaleFT credentials are short-lived, and scoped to a Project, even if a credential is compromised by an attacker, the attacker has a very limited window of time to use the certificate before it expires, and it is only of use against resources in that Project.


