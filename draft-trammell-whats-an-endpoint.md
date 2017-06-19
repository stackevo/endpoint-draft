---
title: What Is an Endpoint?
abbrev: Endpoints
docname: draft-trammell-whats-an-endpoint-latest
category: info

ipr: trust200902
workgroup: Stack Evolution Program
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
  -
    ins: B. Trammell
    name: Brian Trammell
    organization: ETH Zurich
    email: ietf@trammell.ch
  -
    ins: M. Thomson
    name: Martin Thomson
    org: Mozilla
    email: martin.thomson@gmail.com
  -
    ins: L. Howard
    name: Lee Howard
    org: Retevia
    email: lee.howard@retevia.net
  -
    ins: T. Hardie
    name: Ted Hardie
    org: Google
    email: ted.ietf@gmail.com

informative:
  RFC1122:
  RFC1958:
  Saltzer84:
    target: http://dl.acm.org/citation.cfm?id=357402
    title: End-to-end arguments in system design (in ACM TOCS 2(4))
    author:
      -
        ins: J. H. Saltzer
      -
        ins: D. P. Reed
      -
        ins: D. D. Clark
    date: 1984-11-01
--- abstract

what is an endpoint

--- middle

Introduction
============

"Architectural Principles of the Internet"  {{RFC1958}} states:

> It is also generally felt that end-to-end functions can best be realised by end-to-end protocols.

This is an articulation of the end-to-end argument {{Saltzer84}}, which pervades
the architecture of the Internet, and is a key differentiator between the
Internet architecture and the architectures of electronic communications
networks that came before it, as well as the architectures of some networks over which
Internet access is provided. It is often referred to in shorthand in the IETF as
"smart endpoints, dumb middles".

Reaffirming this principle requires us to re-examine what an endpoint is, however,
as there has been significant evolution in the distribution of the functions from which
systems using the network are comprised. Early in the design of the Internet, a
network-layer endpoint was synonymous with a host, and a transport-layer endpoint was
synonymous with a process running on a host.

Changes in the Internet through several decades of development and deployment have complicated
matters.  Many servers now use load balancers, front-end compositors and back-end data stores as
component network end points; some clients, especially in the case of IoT systems, are actually
clusters of devices connected by a gateway.  This draft aims to proposes a new, generalized
definition of an endpoint that recognizes those changes.  It will then explore how it can be
applied to understanding the architecture of the Internet.


Host Requirements Considered Harmful
------------------------------------

\[EDITOR'S NOTE: go ted go]

One reading of the relevant standards is that an endpoint is defined to be synonymous with a host in {{RFC1122}}, and is taken to be anything that meets the requirements specified therein...


Definition
==========

\[EDITOR'S NOTE: This is from Brian's message.]

An endpoint is a necessarily-stateful interface between "the network" (for some definition of "the network") and the entity the network provides communication on behalf of (a user, an application, a device, a service, etc.) This entity is associated with some identity (which may be cryptographically verifiable) and some intent to communicate with some other endpoint(s).

\[EDITOR'S NOTE: This is from Lee's Montreal commit. We should take elements of one or both of these and turn it into the snappy one-liner. Lee's current one-liner is snappier but I think too restricted...]

1. Security endpoint. The point at which a protocol establishing trust is terminated. This may be the point on a web system where a certificate is applied, for example, or the point where an SSH session terminates.
2. Internet endpoint. The point at which the Internet protocol (address, header) is added or removed, but not the point where it is changed. Therefore, a NAT operation (including NAT64, etc.) is not an Internet endpoint, but a Back-to-Back User Agent (B2BUA) is, and a web proxy is. \[DISCUSS]
3. Application endpoint. What a quaint notion!
(continue)

From these specific definitions, one can generalize to the statement:
An endpoint is that function that identifies itself as the target of communication.

\[EDITOR'S NOTE: Introduce subsections]

Statefulness
------------

\[EDITOR'S NOTE: Aaron's comment on the March thread]

An endpoint is where application state lives. For lower layer protocols, the
Internet is generally in service to applications, to hand data to an application
is to hand it to an endpoint. What makes this interesting is that our
prioritization of trust issues has changed, the technologies hosting
applications have become more distributed (in the peripheral, rack, and cloud
senses), and the notion that if one sub-element of an application endpoint
fails, the rest of the application endpoint sub-elements will know (aka fate
sharing) may no longer be valid.

Layering
--------

\[EDITOR'S NOTE: from Lee's commit]

an application endpoint is the process that receives communication from an
application and begins processing it. A network endpoint is the process (or more
loosely, a device) that receives a network packet and processes it. A security
endpoint is the process that responds to communication about security.

Implications of “transport endpoint” being different than “application endpoint”
being different from “security identity”

IoT, Server clusters. Application process != host

To the app, the other end is maybe a hostname, or maybe a process, or maybe a socket API.

But the layered architecture is a strength. You shouldn’t care about the other
end, as long as you can rely on the system when you hand off to the next layer.

Is it as simple as saying, “The L3 endpoint is one thing, the L4 endpoint is
another thing, . . . the L7 endpoint is another thing.” And if so, the L8
endpoint?


Identity
--------

\[EDITOR'S NOTE: Eliot's comment from the March thread]

An endpoint consists of a set of components bound together through a single
identity, through which those components are controlled.  It's an interesting
question because the means by which an endpoint may communicate with others will
vary, and most of our work focuses on interfaces with IP addresses being
endpoints.

Intent and Semantics
--------------------

\[EDITOR'S NOTE: from Natasha]

An endpoint is the closest element to the actor in a use case.

\[EDITOR'S NOTE: from Joe]

An endpoint either initiates network communications or acts as the intended target for such initiations... If the initiator knowingly chose to use a b2bua based on configuration or discovery, then I'd say it was an endpoint.  If it was something the path injected into the flow without user or user-agent awareness, it's not an endpoint.  I think intent of the UA is interesting.

\[EDITOR'S NOTE: from Gabriel]

An endpoint is a participant in a semantic dialog.


Distribution
------------

\[EDITOR'S NOTE: This is from Ted's comment on the 14.6. IAB call. Clean this up a bit.]

The cooperative middlebox, if you have a split server where the server is doing some of the work at the front and some at a series of backends. Might be as far in as the thing that serves the actual data. In QUIC you have this model where if you try and say the end points are talking to each other, you're collapsing a bunch of cooperative systems into something called an end point. But we've traditionally thought of services as client to server or endpoint to endpoint, but that may be too simple. Some of the endpoint people in the IOT space may not see the mirroring, so I think the 00 will be useful for saying this is happening at both ends.


Illustrations
=============

Content Distribution Networks
-----------------------------

write me

Gateways between IP and non-IP networks
---------------------------------------

write me

Configured application-layer proxies
------------------------------------

write me

Rendezvous
----------

write me

Other Sources
=============

- Joe Touch's UDP Tunnels draft
- Anything to take from Dave Dolson's draft on what middleboxes do?
