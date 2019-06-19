---
title: HTTP Components
date: 2018-12-06 12:00:00 Z
permalink: "/http.html"
description: HTTP components used in the 402-Receipt Proposed standard.
documentation_order: 4
summary: Documentation of HTTPS headers and response codes used in the 402-Receipt
  Proposed standard.
---

Most of the communication needed by this standard happens in the HTTP headers of requests and responses.  

Additionally, the meaning of relevant HTTP Response codes is explained.

**All requests and responses involved in this standard should be made over HTTPS connections with valid certificates.** Implementations are not obliged to accept receipts or other information transmitted over HTTP.

{% include glossary_item s=site.data.glossary.accepts_header %}
{% include glossary_item s=site.data.glossary.receipt_header %}
{% include glossary_item s=site.data.glossary.402_response %}

