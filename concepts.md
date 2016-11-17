---
title: "Concepts"
menu:
  main:
    parent: 'reference'
    weight: 1
---
### Client

The ScaleFT client is installed on a device (such as a laptop or workstation) which a user uses to access infrastructure. The ScaleFT client manages the dynamic credentials on the device so the user can transparently access ScaleFT-managed infrastructure.

[Client Enrollment documentation]({{% relref "enrolling-a-client.md" %}})


### Group

A group is a collection of users and team permissions. Groups are linked to projects to describe Users' permissions within that project.

[Group documentation]({{% relref "groups.md" %}})


### Identity Provider (IdP)

Every Team has an Identity Provider which Users authenticate to using the Team's authentication method. The IdP is the source of truth for that User's identity and current access.


### Project

A Project is a collection of resources (such as servers, load-balancers, web services, or VPNs) that share configurations and associated User Group permissions.

[Project documentation]({{% relref "projects.md" %}})


### Service User

A Service User is a member of a Team. Service Users can belong to multiple Groups. They are used for automating actions against the ScaleFT API. They are not granted credentials to servers.

[Service User documentation]({{% relref "service-users.md" %}})


### Team

A Team is a group of people who work together on infrastructure and share an authentication method (such as OAuth).

[Team documentation]({{% relref "teams.md" %}})


### User

A User is a member of a Team. Users can belong to multiple Groups and have multiple clients.

