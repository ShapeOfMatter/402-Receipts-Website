---
title: Compression
date: 2018-12-31 15:44:00 Z
permalink: "/compression.html"
description: Conventions for compressing objects within the context of the 402-Receipts
  standard.
documentation_order: 8
summary: Exact specification of how larger objects should be compressed, for example
  for use in HTTPS headers.
---

There are a few places throughout the standard, particularly in HTTPS Headers, where compression is required.  
Usually this is to reduce the likelihood of problems with HTTPS Header size limits. The parties are strongly recommended to check the size of the compressed string against a reasonable limit (10KB for an HTTPS Header); if no remediation for an over-sized message is available it may be better to throw a run-time exception than to send messages that can't be received. 

The data, as UTF-8, should be compressed in zlib format and then rendered as base64.  
As an example, in python3 we'd have a library like this (for string-to-string compression):

```python3
#!/usr/bin/env python3
import base64
import zlib

def compress(plaintext_string):
  return base64.b64encode(zlib.compress(plaintext_string.encode(), 9)).decode()

def uncompress(b64_string):
  return zlib.decompress(base64.b64decode(b64_string.encode())).decode()

```

- Is the above description sufficiently specific? A Haskell code example would make the bytewise representation more explicit.
- Is zlib the ideal compression scheme? gzip is basically just as ubiqutious and it's what the HTTP body will typically use. On the other hand gzip libraries seem to be written for "files", and it's better here to work with "strings". 
- Should this compression be optional? After all, even an uncompressed {% include link s=site.data.glossary.receipt_definition %} will typically be less than 10KB. If we make it optional, do we need any kind of flag to denote compression?
