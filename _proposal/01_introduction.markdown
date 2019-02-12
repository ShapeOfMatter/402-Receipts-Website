---
title: Introduction
date: 2018-12-06 12:00:00 Z
permalink: "/introduction.html"
description: The 402-Receipt Proposed standard.
documentation_order: 1
---

# Version negative one.

> #### Goal of this document:
>
> This document describes a standard way for a website to demand or accept payment for access to resources without having a prior relationship with the customer or at any point collecting any card/bank information. The proposed standard is a suite of HTTPS headers, HTML head elements, and surrounding utilities to make direct monetization of web-accessible resources low-stress and safe even for non-specialist human users.
>
> The standard needs to be sufficiently defined that tools within it can be built independently and work together. It must be a suitable tool for producers and consumers, so if you have questions, ideas, or suggestions about the technical details or about the high-level user experience then please reach out to us. 

## How to help
This website is on [GitHub](https://github.com/ShapeOfMatter/direct-monetization-static); pull requests are welcome. You can also email us with questions or suggestions at <dmn@directmonetization.network>.
We'll move to our own website an domain as soon as we're sure we have a good name.

## The name
The 402 HTTPS response code implies that a request is being denied because payment must be provided for the requested resource. [No standard way of following up to a 402 response has been normalized](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#402). The 402 response code has seen only niche usage, mostly for subscription-only APIs, and is effectively non-standard for human-facing HTTPS resources. This standard will fix that.

## Table of contents:
{% assign pages = site.proposal | sort: 'documentation_order' %}
{% for p in pages %}{% if p.summary and p.documentation_order %}
  - [{{ p.title }}]({{ p.url }}) — {{ p.summary }}
{% endif %}{% endfor %}

