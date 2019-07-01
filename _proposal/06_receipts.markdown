---
title: Receipts
date: 2018-12-06 12:00:00 Z
permalink: "/receipts.html"
description: The 402-Receipt Proposed standard.
documentation_order: 5
summary: How receipts are composed, signed, used, and validated. (work in progress)
---

A Receipt is a message specifying that someone paid for access to a resource, or should otherwise be given access to the resource.

> There are some practical limitations of the readily available cryptographic options, which are unlikely to be fixed in time for version 0.  
> In particular, the use of a _fully_ blind signature means that, in practice, a given Notary can only issue Receipts for a single amount.
> Like other performance issues, we _do_ plan to address this problem, but useable systems don't need to wait for it.

{% include glossary_item s=site.data.glossary.receipt %}

> Systems to prevent sharing of receipts are desired, but not critical for version 0.

## UUID Details
It's the Client's responsibility to generate a random version-4 UUID.
Use of other UUID types may result in identifiers that are traceable back to the Client's computer, or may risk collisions.
Uniqueness is only enforceable on the signer/domain/UUID _triplet_;
the global uniqueness of UUID's can't be relied upon here because a malicious client could deliberately violate it.

## Bundled Receipts

The `receipts` XML object is a _list_ because situations are likely in which a user will want to submit multiple
receipts at once.
For example, a website might give Receipt Definitions to the effect of _"Pages are \$0.05 each, up to \$3.00/month."_. 
Once a customer had viewed enough pages that their receipts for that month totaled \$3.00, 
their Client would begin submitting bundled Receipts instead of buying a receipt for each page.

The above configuration would be accomplished by serving two Receipt Definitions with each page;
the first (\$0.05) would specify the page as the `item`, and the second (\$3.00) would have a blank (wildcard) `item`
field.

## Schema

{% include xsd.table xsd=site.data.402_receipts_receipt_xsd %}
