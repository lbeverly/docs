---
title: "Concepts"
menu:
  main:
    parent: 'reference'
    weight: 1
---
### Client

The ScaleFT client is installed on a device (such as a laptop or workstation) which a user uses   to access infrastructure. The ScaleFT client manages the dynamic credentials on the device so the user can transparently access ScaleFT-managed infrastructure.

[Client Enrollment documentation]({{% relref "enrolling-a-client.md" %}})


### Group

A group is a collection of users and team permissions. Groups are linked to projects to describe  users' permissions within that project.

[Group documentation]({{% relref "groups.md" %}})


### Identity Provider (IdP)

Every team has an Identity Provider which users authenticate to using the team's authentication   method. The IdP is the source of truth for that user's identity and current access.

[//]: < no link to additional information for Identity Provider (IdP)>

### Project

A project is a collection of resources (such as servers, load-balancers, web services, or VPNs)   that share configurations and associated user group permissions.

[Project documentation]({{% relref "projects.md" %}})


### Service User

A service user is a member of a team. Service users can belong to multiple groups. They are     used for automating actions against the ScaleFT API. They are not granted credentials to
servers.

[Service User documentation]({{% relref "service-users.md" %}})


### Team

A team is a group of people who work together on infrastructure and share an authentication method (such as OAuth).

[Team documentation]({{% relref "teams.md" %}})


### User

A user is a member of a team. Users can belong to multiple groups and have multiple clients.

[//]: <no link provided to additional documentaion for user>
