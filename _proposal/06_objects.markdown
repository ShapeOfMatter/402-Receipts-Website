---
title: XML Definitions
date: 2019-01-12 12:00:00 Z
permalink: "/xml.html"
description: XML schema documentation for the 402-Receipt Proposed standard.
documentation_order: 6
summary: Detailed descriptions of XML objects used to communicate required receipts.
---

Here we provide detailed explanations of how the XML objects used in this standard are built, and what they represent.

{% include glossary_item s=site.data.glossary.menu_xml %}
{% include glossary_item s=site.data.glossary.receipt_definition %}
{% include glossary_item s=site.data.glossary.bare_receipt %}
{% include glossary_item s=site.data.glossary.signed_receipt %}
{% include glossary_item s=site.data.glossary.submittedreceipt %}

## Examples
Here's a small Receipt Definition in its entirety.

```xml
<definitions xmlns="https://402.TBD">
  <definition>
    <domain>https://www.example.com/</domain>
    <item>/path/image.png</item>
    <signers>
      <signer>https://receipts.dmn.network/path</signer>
    </signers>
    <ttl>2720000</ttl>
    <fresh>60</fresh>
    <costs>
      <cost>
        <units>USD</units>
        <amount>0.05</amount>
      </cost>
    </costs>
  </definition>
</definitions>
```

This must be [compressed]({{ "/compression.html" | relative_url }}) to be used in a {% include link s=site.data.glossary.accepts_header %}.

```text
Receipts-Accepts: eNpVkFFugzAQRP97CpQDeBFqWqna+qPKDdoewCIbsIrXFrsROX4MhpD6a954PFovnuni2auPLNUtDCyfh141yQfAa92Yn6/Twb5UFe65GWcjBufZbuFpmgzdXEgDmTYGQFgDJe2VgoXktAcfXEcmcYewuCUgvmMapdCDH/UjteSTijkHNkw6xfFvqUNYk6UG/vWg6mCb96bOB2GGYl9Gkt6+Za+o4rZRdB9gpg0yXvPnxf5+nxCK3K9ciFdWW5v6iLDC1gJ7TdHLw7ycp3U+k9g7Cyp50Q==
```

We provide two example {% include link s=site.data.glossary.menu_xml %} files. These links go directly to the xml files.

- [/menu_example_small.xml](/menu_example_small.xml)
- [/menu_example_large.xml](/menu_example_large.xml) (Also shows a broader variety of Receipt Definitions)
