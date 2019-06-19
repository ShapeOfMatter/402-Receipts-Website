---
title: Receipts
date: 2018-12-06 12:00:00 Z
permalink: "/receipts.html"
description: The 402-Receipt Proposed standard.
documentation_order: 5
summary: How receipts are composed, signed, used, and validated. (work in progress)
---

A receipt is a message specifying that someone paid for access to a resource, or should otherwise be given access to the resource.

> There are some practical limitations of the readily available cryptographic options, which are unlikely to be fixed in time for version 0.  
> In particular, the use of a _fully_ blind signature means that, in practice, a given Notary can only issue Receipts for a single amount.
> Like other performance issues, we _do_ plan to address this problem, but useable systems don't need to wait for it.

There are several objects nested inside each other that, in different circumstances, might each be called a receipt.

{% include glossary_item s=site.data.glossary.bare_receipt %}
{% include glossary_item s=site.data.glossary.signed_receipt %}

> Systems to prevent sharing of receipts are desired, but not critical for version 0.

## Bundled Receipts

> A system for submitting multiple Receipts in a single request _is_ critical for version 0, but isn't resolved yet.

In the case that the Client should have access because of previously submitted payments they have made _for other resources_, 
a list of the `uuid`s of those receipts may be used in place of the Signed Receipt in the Receipt Submission.

For example, a website might give Receipt Definitions to the effect of _"Pages are \$0.05 each, up to \$3.00/month."_. 
Once a customer had viewed enough pages that their receipts for that month totaled \$3.00, 
their Client would begin submitting Bundled Receipts instead of buying a receipt for each page.
