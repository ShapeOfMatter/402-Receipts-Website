---
title: Overview
date: 2018-12-06 12:00:00 Z
permalink: "/overview.html"
description: Overview of the 402-Receipt Proposed standard.
documentation_order: 2
summary: An overall summary of how the system works.
---

We propose a suite of HTTPS headers, HTML head elements, and surrounding utilities to make direct monetization of web-accessible resources low-stress and safe even for non-specialist human users.

> We anticipate a tip-jar configuration in which no payment is _required_ to access the resource, but a clear means of making optional payments is exposed to the client along with explicit expectations about what they _should_ pay. Throughout this document we will talk interchangeably about "requiring" or "accepting" receipts. The actual behavior gets specified in the {% include link s=site.data.glossary.receipt_definition %}. Tools for handling this situation _within the tools of this protocol_ and _with ideal performance_ are unlikely to be included in Version 0.

Although this standard will focus on HTTPS exchanges; it's desirable that the framework translate clearly to other internet communications. 

## How do you, an end-user, use this?


> #### The very short version:  
> You'll sign into an account in a network and, as you browse the web, sites in that network will automatically charge you small amounts for each page you access. You're protected from fraud and abuse by the network, while the websites get a strong, unobtrusive paywall (or tip-jar).  
> The protocol itself masks your browsing activity from the network (the Notary).

In order to participate, you'll need to create an account with at least one {% include link s=site.data.glossary.notary %}. You'll need your web-browser to be logged into some sort of {% include link s=site.data.glossary.wallet %}; this will probably be a browser plugin, but we want to have javascript/cookie based options too. The wallet is the only part of the system that both knows who you are _and_ what you're doing.  
If you aren't logged in properly, you may see prompts or placeholders as you browse the web.

As you browse the web, websites you visit will tell your web-browser how much their pages cost. They do this using Header tags in the 
underlying HTTPS responses that direct your browser to get a Receipt from the Notary; this happens in the background without you needing to do anything.

When you navigate to a page that costs money, if your wallet is configured to allow the transaction (based on the amount and any details about the website itself), then it will fetch a receipt for the needed amount from the Notary.
This receipt is passed to the website, which then gives you access to the page or content in question. This happens in the background without you needing to do anything; as a human user you only need to worry about the payments system when you're configuring your accounts.

### Context for a 402 response
It's generally poor user experience to reject a web-page request outright. (A {% include link s=site.data.glossary.402_response c="402 Response" %} to such a request may work if a suitable placeholder page is available and the {% include link s=site.data.glossary.client %} is trusted to handle the response appropriately.)
In practice, it is usually better to give a normal response to the principal request and require receipts for a key resource used by that page, for example an image or text-block.

### Consumer tools:
We anticipate a distinction between the {% include link s=site.data.glossary.client %} (typically a web-browser, possibly with a plugin) and a remote {% include link s=site.data.glossary.wallet %} which will allow persistence of user-data between clients and devices.

### Producer tools:
Different {% include link s=site.data.glossary.host c="Hosts" %} will have different needs. 
Typically there will be a server plugin, designated servlet, or specialized CDN, 
that will inspect requests for receipts, validate the receipts, and forward them to their respective Notaries for disbursement. 

### Brokers and Networks:
Throughout this standard we speak of a {% include link s=site.data.glossary.notary %}. The Notary's role is not just to sign receipts; they also handle the collection of money from consumers and disbursement of it to producers. In the typical case both the host and the client will have a prior relationship (membership or account) set up with one or more Notary; as long as they have one in common the user experience can proceed seamlessly.
