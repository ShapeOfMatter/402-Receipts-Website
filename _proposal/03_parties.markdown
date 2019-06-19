---
title: Parties
date: 2018-12-27 16:00:00 Z
permalink: "/parties.html"
description: Description of the roles of the Client, Host, and Notary.
documentation_order: 3
summary: Describes the roles of the Client, the Host, and the Notary. Also outlines
  the behavior of the tools they'll use.
---

## The Client
Because the 402-Receipts system is designed to be used passively by the human user, we mostly speak in terms of the Client (the web-browser).  
{% include glossary_item s=site.data.glossary.client %}

Existing web browsers don't have the behavior defined in this standard, so the user will need to install a browser plugin.

> Javascript included on pages served may be able to act as the Client; this would be good because it would be easier for some users.
> We need a clear idea of _how_ that can work, and how it can support the same privacy and trustworthiness guarantees
> before we can promise that it will be an option.

{% include glossary_item s=site.data.glossary.wallet %} 

It's desirable to include the communication between the Wallet and the Client in this standard,
firstly because independently created Clients (for example a Firefox plugin and an Android app) should be able to use a common Wallet,
and secondly because a safe standard for Wallet communication will be critical to an in-page javascript Client implementation. 

## The Host
The Host is the computer (the server) which provides the web pages to the Client. 
The Host is _not exactly just_ "the website", although this is an OK layperson's approximation.
{% include glossary_item s=site.data.glossary.host %}

We assume that the Host's address will match the `domain` (and often `item`) of the Bare Receipt, and this may be enforced by the Client or Notary.

Assuming we stick with a blind-signature scheme for [Receipts]({{ "/receipts.html" | relative_url }}), a truly static Host will not be able to use this standard.
At absolute minimum the host will need to be able to strip the identifying key and signature and forward the receipt and Notary signature to the Notary;
otherwise the Notary would never know to pay the Host.  
In practice, the Host should also be obliged to validate the receipt as part of request handling, and the Host **should not** forward the receipt until handling of the HTTPS request in question has finished. Submitting receipts to the Notary in batches (for example, every hour) can (in conjunction with some defensive behavior on the part of the Clients) prevent deanonymization of Receipts by timing analysis. 

Furthermore, Hosts will generally need to maintain a database of receipts received which are still valid for reuse, along with the Client Key they were originally submitted with.
This is needed to prevent sharing of receipts between consumers.

## The Notary
The Notary is a third party, analogous to a traditional monetization platform but fundamentally less powerful. The Notary sells Receipts to Clients; the Receipts are used to access websites.
{% include glossary_item s=site.data.glossary.notary %}

Of course it's the Notary's responsibility to make themselves valuable to the other parties,
but it's illuminating to explain here some of the ways they might do that.

- The Notary will generally relieve the Host of payment processing complexity, and account-management more generally.
- When a Host joins a Notary's network, they hope to receive payments from a wide audience of consumers; the Host can focus on _traffic_ and _audience retention_ instead of a _sales funnel_. 
- The Notary can protect the Client from abusive Hosts in various ways, including proactive monitoring of member Hosts and post-hoc remediation. (Point-of-sale protections are generally not feasible for the Notary, as receipt signatures are issued blindly. Such protections can be built into the [Wallet]({{ "client.html" | relative_url }}).)
- For a Client to set up an account with a given Notary generally constitutes pre-authorization of certain kinds of payments for certain kinds of resources. In this sense Notaries act like "channels" to which a user can subscribe.

In practice, we only anticipate two kinds of Notaries.

- A Host could be their own Notary. This could accomplish any of the same functionalities as existing paywalls offer, although the standardized machine interface would enable smoother user-experiences. 
- **A Notary can act as a network, channel, buyer's club, or federation.** Many Hosts and many Clients are assumed to have prior arrangements (accounts) with a given Notary; this is the Notary's network. As long as a Host and Client have a network in common, payment for resources can typically proceed _automatically_.

Notaries with larger networks will obviously have an advantage toward attracting new members of both kinds.  
On the one hand, the variety of use-cases this standard can accommodate, and the variety of legal, technical, and business paradigms people operate in, will likely ensure a plurality of Notaries. On the other hand, it is still desirable to include protections _against the Notaries_. Consumers are presumed to have given their payment processing information (a debit card, for example) directly to the Notary, but privacy of their data can still be protected by insisting on a blind-signature scheme, and by proper design of Wallets and Clients. Producers (Hosts) can best be protected by making sure self-Notarization is a viable option (although this does put the onus of payment processing back in their lap).

{% include glossary_item s=site.data.glossary.canonical_url %}
