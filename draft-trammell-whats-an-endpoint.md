---
title: What is an endpoint
abbrev: Endpoints
docname: draft-trammell-whats-an-endpoint-latest
date: 2017-05-23
category: info

ipr: trust200902
area: General
workgroup: XMPP Working Group
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

--- abstract

what is an endpoint

--- middle

Introduction
============

As articulated in RFC1958, "Architectural Principles of the Internet:"
  
     It is also generally felt that end-to-end functions can best be realised by end-to-end protocols.

This statement can only be applied if one can determine what an "end" is.

 see Joe Touch’s UDP tunnels draft 
 Dave Clark's end-to-end principle, 
 draft-dolson-plus-middlebox-benefits)
Implications of “transport endpoint” being different than “application endpoint” being different from “security identity”	
	IoT, Server clusters. Application process != host
	To the app, the other end is maybe a hostname, or maybe a process, or maybe a socket API.
	But the layered architecture is a strength. You shouldn’t care about the other end, as long as you can rely on the system when you hand off to the next layer.
	Is it as simple as saying, “The L3 endpoint is one thing, the L4 endpoint is another thing, . . . the L7 endpoint is another thing.” And if so, the L8 endpoint?

On the other hand, an endpoint is defined to be synonymous with a host in {{RFC1122}}, and is taken to be anything that meets the requirements specified therein.

This implicit definition is inadequate for reasons.

We present a new one, and the rationale behind it, for reasons.

Definition
==========


write me -- endpoint is identity with intent etc etc
1. Security endpoint. The point at which a protocol establishing trust is terminated. This may be the point on a web system where a certificate is applied, for example, or the point where an SSH session terminates.
2. Internet endpoint. The point at which the Internet protocol (address, header) is added or removed, but not the point where it is changed. Therefore, a NAT operation (including NAT64, etc.) is not an Internet endpoint, but a Back-to-Back User Agent (B2BUA) is, and a web proxy is. [DISCUSS]
3. Application endpoint. What a quaint notion!
(continue)

From these specific definitions, one can generalize to the statement:
An endpoint is that function that identifies itself as the target of communication.

Thus, an application endpoint is the process that receives communication from an application and begins processing it. A network endpoint is the process (or more loosely, a device) that receives a network packet and processes it. A security endpoint is the process that responds to communication about security. 

Host Requirements Considered Harmful
------------------------------------

go ted go

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
