---
title: SSH Architecture
include_mathjax: true
menu:
  main:
    parent: 'reference'
    weight: 3
---


******************************************************************************
## Public Key Authentication

SSH provides a mechanism to authenticate users with public/private key pairs.<sup>([1])</sup>
The user has a private key, and they provide their public key to the server.
When the user attempts to login, the server sends a session identifier to the
client. The client can then prove that it has a secret key by generating a
digital signature which contains this random session identifier and the public
key.<sup>([2])</sup> If the user can prove they have the private key of a public key that
the server knows to authorize, they are authenticated. 

This mechanism for authentication is considerably more secure than using
passwords, because the difficulty of guessing a password is fairly trivial
compared to the difficulty of guessing a private key.<sup>([3], [4], [5])</sup>

Public key authentication is not ideal though, and has its own challenges. For
one, the server must be made aware of the public keys to authorize in advance.
For another, the server has no control over how the user secures their private
key. The user is free to use a weak password, or even a completely unencrypted
(no password) private key. 

******************************************************************************
## Certificate Based Authentication

Certificate based SSH authentication is essentially an extension to public key
authentication.<sup>([6])</sup> However, with certificate based authentication, the
server is not required to know the public key in advance. Instead, the server
is configured with a trusted Certificate Authority (CA) certificate, and it
uses that certificate to validate that a client's public key has been signed by
that trusted CA. This way, the user presents both their public key, and proof
that they have the private key corresponding to that public key all in one
step.  (The public key is included in the message the client signs to prove it
has the private key.) This method of authentication is a significant
improvement over "regular" public key authentication because every server you
have does not need to be made aware in advance of every public key it should
authorize.

However, there are still some problems to be addressed. Specifically,
servers blindly trust any signed key for the duration of that signature, and
synchronizing revocation lists or otherwise revoking certificates is
non-trivial. Further, there is still no control over the private keys being
used, nor how well protected those keys are. For example, a user could have checked their
private key into a public git repository, and for the lifetime of
the certificate, anyone can use it to login.

ScaleFT uses certificate based authentication, and solves the problems of key
management and certificate revocation by issuing ephemeral credentials with
certificates that expire within minutes. No revocation lists are
required because *every* certificate we issue expires within minutes, and so
are "revoked" automatically. Because keys are also ephemeral, and
only ever signed once, if a user went out of their way to grab one and commit
it into a public git repository, that key is rendered useless within minutes.

******************************************************************************
## Host-key Validation

Authenticating that a user is who they claim to be is obviously important, but
it is equally important that the user verify the authenticity of the host they
are connecting to.<sup>([7])</sup> If the user cannot authenticate the host they are
connecting to, all the user-validation in the world is easily circumvented with
something called a "Man-in-the-Middle" (MitM) attack.<sup>([8], [9])</sup>

<img alt="MitM" src="/docs/static/MitM.png" style="max-height: 142px;" />


While MitM attacks are somewhat confounded by the fact that session-ids are
negotiated via key-exchange algorithms<sup>([10])</sup> and public key authentication
requires that the session-id be included in the signed message<sup>([2])</sup>, such
attacks are still possible (e.g., in cases where you forward your ssh-agent to
the malicious host, or in cases where a weak KEX is used<sup>([11])</sup>). Essentially,
the user's client connects to a machine they believe is the target-host, but is
really just a server that pretends to be that target-host.  This imposter
(the MitM) uses whatever mechanisms it can to authenticate as the user; either
by exploiting the user's forwarded ssh-agent, or by *somehow* forcing the
negotiation of the same session-id it already negotiated with the target-host.
Once logged in, this MitM can do anything it likes up to, and including sending
any commands it wants as though the user had input them; all without ever
seeing the private key.

The SSH Protocol has a solution for this problem, it is called host-key
validation, and it is essentially the same thing as the Public Key
Authentication explained above, but backwards. The server authenticates itself
to the client by proving that it has the private key corresponding to a public
key known to the client. The problem with this solution is that the public key
must be known to the client in advance. (Just as with public key authentication
before certificate based authentication.) As a solution to this,
certificate-based host-key validation is also supported in openssh, but getting
revocations to client machines is considerably less reliable than getting them
to servers, which was already a hard problem.

By providing a secure, out-of-band mechanism to exchange the public key of all
your hosts, ScaleFT ensures that your SSH client will always have the correct
host-keys necessary to authenticate target hosts and establish a secure
connection. This completely avoids the "Trust On First Use" (TOFU) problem most
SSH users experience the first time they connect to a host, and they must
blindly trust that the key they are presented with is valid for that host.

{{% terminal %}}
<div>The authenticity of host 'web0.example.com (198.51.100.12)' can't be established.
RSA key fingerprint is SHA256:v8SbZC97NSdqqj8rEJ+dvK7yh47ex53n8vVfW8Lf/G0.
Are you sure you want to continue connecting (yes/no)?</div>
{{% /terminal %}}

ScaleFT obtains the server's public host key directly from the source, and then
ensures your client is configured with that public key, all securely over TLS
at every step.

Before ScaleFT, you may have just accepted:
{{% terminal %}}
<div>@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!</div>{{% /terminal %}}

as something you see when you re-image a machine, or spin up a new instance
with the same name as a prior instance, with ScaleFT this warning becomes rare,
meaningful, and you should definitely not proceed if you see it.

******************************************************************************

[1]: https://simple.wikipedia.org/wiki/Public-key_cryptography
[2]: https://tools.ietf.org/html/rfc4252#section-7 
[3]: https://help.ubuntu.com/community/SSH/OpenSSH/Keys
[4]: https://en.wikipedia.org/wiki/Password_strength
[5]: https://en.wikipedia.org/wiki/Key_(cryptography)
[6]: http://cvsweb.openbsd.org/cgi-bin/cvsweb/src/usr.bin/ssh/PROTOCOL.certkeys?annotate=HEAD
[7]: http://link.springer.com/chapter/10.1007/978-3-0348-8295-8_17
[8]: https://www.giac.org/paper/gsec/2034/conducting-ssh-man-middle-attacks-sshmitm/103515
[9]: https://www.blackhat.com/presentations/bh-usa-03/bh-us-03-ornaghi-valleri.pdf
[10]: https://simple.wikipedia.org/wiki/Diffie-Hellman_key_exchange
[11]: https://weakdh.org/
