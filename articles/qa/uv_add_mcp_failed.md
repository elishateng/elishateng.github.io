---
layout: page
title: uv add mcp failed
categories: qa
description: uv add mcp failed
keywords: qa
permalink: /articles/qa/uv_add_mcp_failed
---

## Question
```
$uv add mcp[cli]
⠼ mymcp==0.1.0
  × Request failed after 3 retries
  ├─▶ Failed to fetch: `https://pypi.org/simple/mcp/`
  ├─▶ Request failed after 3 retries
  ├─▶ error sending request for url (https://pypi.org/simple/mcp/)
  ├─▶ client error (Connect)
  ╰─▶ invalid peer certificate: UnknownIssuer
  help: Consider enabling use of system TLS certificates with the `--native-tls` command-line flag
```

## Answer

Open ~/.bashrc, add the following commands:
```
export SSL_CERT_DIR=/etc/ssl/certs
export REQUESTS_CA_BUNDLE=/etc/ssl/certs/ca-certificates.crt
```

## Reference:
[How to run uv behind a corporate proxy?](https://github.com/astral-sh/uv/issues/1474)
