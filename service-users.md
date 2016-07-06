---
title: "Service Users"
menu:
  main:
    parent: 'none'
    weight: 3
---

ScaleFT uses service users to allow you to build automation against the
ScaleFT API. This could include operations such as:

1. Adding users to groups programmatically.
2. Retrieving audit event logs to store in your ELK setup.

Service users can be added to a group just like a normal user, and they
will be granted permissions the same way. Currently the main difference
between a user and service user is how each type of user authenticates.

While users are backed by an Identity Provider(IdP), a service user is
given a pair of credentials that are used to generate a short-lived
authentication token to be used with the API.

<div class="alert alert-warning">
Important: Service users are not able to create credentials to access servers.
</div>

## Authentication

In order to authenticate as your service user to the ScaleFT API, you will need to create an
API key. The API key is a pair of strings known has the Id and Secret.
You will need both to authenticate, which generates an authentication
token that is sent with each request you make.

Follow these steps to create an API key:

1\. Nagivate to the details for your service user
<img src="/docs/static/view-a-service-user.png" style="max-height: 621px;" />

2\. Confirm the creation of your API key
<img src="/docs/static/create-service-user-api-key.png" style="max-height: 621px;" />

3\. You will be presented with your API key secret. Copy it down to a safe place.
<img src="/docs/static/service-user-api-key-rotated.png" style="max-height: 621px;" />
<div class="alert alert-info">
Note: When you create an API key, you will only be able to see the secret once. Store it securely!
</div>

### Expiring API Keys

Whenever a new API key is created, any existing API keys will be
automatically expired in 2 days. You can also immediately expire an API
key so it can't be used anymore.

1\. Click the red "Expire" button next to the key you would like to get rid of
<img src="/docs/static/created-api-key-for-service-user.png" style="max-height: 621px;" />

2\. Confirm the dialog to expire the API key.
<img src="/docs/static/expire-service-user-api-key.png" style="max-height: 621px;" />
<div class="alert alert-danger">
Note: Expiring an API key immediately will prevent any requests using a token generated with it from succeeding.
</div>
