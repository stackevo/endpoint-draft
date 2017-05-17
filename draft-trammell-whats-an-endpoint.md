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

The Internet provides connectivity between endpoints

"It is... generally felt that end-to-end functions can best be realised by end-to-end protocols." {{RFC1958}}

An endpoint is defined to be synonymous with a host in {{RFC1122}}, and is taken to be anything that meets the requirements specified therein.

This implicit definition is inadequate for reasons.

We present a new one, and the rationale behind it, for reasons.

Definition
==========

one-sentence definition goes here, then explain it.

two key concepts: identity and intent. identity is addressing + authentication. intent is either intent to initiate or to accept communication using some protocol for some purpose. point out that both identiy identity binds more readily to process than to host. 

layering and tunneling: yep.

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
