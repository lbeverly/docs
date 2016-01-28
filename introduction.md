---
title: "Introduction to ScaleFT"
menu:
  main:
    parent: 'user-guide'
    weight: 0
---

## Overview

ScaleFT is a cloud-native security platform that brings risk-based, dynamic authentication to cloud infrastructure using short-lived certificates.

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

### Identity Provider (IdP)

Every Team has an Identity Provider which Users authenticate to using the Team's authentication method. The IdP is the source of truth for User's identity and current access.

## Architecture

ScaleFT is composed of three components:

* ScaleFT Platform
* ScaleFT Daemon
* ScaleFT Client

Deploying ScaleFT in your infrastructure is as simple as deploying the ScaleFT Daemon on your servers, and installing the ScaleFT Client on any workstation which is permittted to access your infrastructure.

### ScaleFT Platform

The API and web dashboard that enable configuration, communication, and coordination across all ScaleFT components.

### ScaleFT Daemon

The multi-OS, host-local agent that interfaces with the server's local services and user accounts to enable ScaleFT features like certificate-based authentication, user account auto-creation, and superuser privileges.

Unlike older approaches to authentication, this agent is not involved in the active authentication processes of services on the server. ScaleFT certificates can already be cryptographically verified by SSH and services which use X.509 independently of `stfd`.

### ScaleFT Client

The application that users install to interface with their workstation's local cryptographic stores and enable dynamic authentication workflows.

## Short Lived Certificates

ScaleFT Projects operate Certificate Authorities to issue short-lived certificates, which are managed transparently on the User's device by the ScaleFT Client.

Each of these certificates contains the following information:

1. The ScaleFT Project for which the certificate was issued
2. The username to be used on the server of the Scaleft User to whom the certificate was issued
3. The time at which the certificate expires

Before a certificate expires, the ScaleFT Client will re-verify that the User should continue to have access, and as long as the user remains authenticated and authorized, the Client will automatically install a renewed certificate valid for another brief interval.

Since ScaleFT credentials are short-lived, and scoped to a Project, even if a credential is compromised by an attacker, the attacker has a very limited window of time to use the certificate before it expires, and it is only of use against resources in that Project.


