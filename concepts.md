---
title: Overview of Concepts
---

# Components

ScaleFT has 3 major components: the Platform, Server Integrations, and Clients.

## Platform

Hosted service that provides the web application and APIs for ScaleFT. The platform is available as both a multi-tenant SaaS or as a private edition appliance.

## Server Integration

Daemons for installation on servers which provide data and integration with the platform.

## Clients

Client applications that integrate ScaleFT into the user's operating systems.

# ScaleFT Access

ScaleFT Access is a Certificate Authority (CA) that provides fast-expiring certificates for your users to access protected resources.

## Certificate Authority (CA) Overview

A Certificate Authority, commonly abbreviated "CA", is a service that issues digital certificates.  One way to think about a certificate is as a key/value document that has been signed by a third party.  Acting as this third party, CAs cryptographically sign the document. The document contains the "Subject Name" and "Public Key" of the certificate's owner. The certificate and the associated private key can be used to prove the identity to another service, without that service needing to contact the CA.  Using this information, software can use ["Public Key Infrastructure"](https://en.wikipedia.org/wiki/Public_key_infrastructure) with protocols like [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) to bootstrap from slower asymmetric public/private key operations to faster symmetric ciphers like AES.

### Traditional CAs

CAs are widely used to power HTTPS websites on the Internet. Browsers and operating system comes setup with a set of trusted issuing CAs. Many websites with use cases from e-commerce to email use a certificate issued by these trusted CAs. Standards like PCI-DSS require that websites use HTTPS so that sensitive data like credit cards is encrypted in transit, and so that an attacker cannot perform a [man-in-the-middle attack](https://en.wikipedia.org/wiki/Man-in-the-middle_attack).

For website use cases, certificates contain a subject name with the URL of the website, and the pubic key of a private key controlled by the website operator. An issuing CA validates the operator controls the website, and then issues a signed certificate attesting to this.  When a user navigates to a website, their browser validates that this certificate is from a trusted issuing CA, and that it hasn't expired or been revoked.  The certificate is meant to prove the identity of the website to the user's browser, but does not attest to any information to the website about the user.

### Client Focused CAs

Built into the TLS protocol is support for clients to also provide certificates -- that is to attest to a server information about the client.  For example, you could get a client certificate attesting that your email address is `alice@example.com`, and if the server trusted this certificate, it could use it as your login to email.

Traditionally client certificates have not been used as widely as server certificates because of a few problems:

* Attesting facts about clients requesting client certificates is difficult for the issuer.
* The are long-lived. Typically client certificates are long-lived to save the user the burden of frequently re-acquiring certificates. Unfortunately the longer-lived the certificate, the less secure it is.
* They are hard to configure.
* Revocation of client certificates is complicated.

## ScaleFT Access's Approach

### Compared to Passwords

* Passwords are static, commonly re-used.
* Cleartext to server (compromised server can use)
* Even with a password manager, once compromised an attacker can use them forever.

### Compared to Asymmetric Keys

Both traditional Client Certificates and SSH public keys share these difficulties:

* Long-lived
* Depend on user expertise to be handled consistently


