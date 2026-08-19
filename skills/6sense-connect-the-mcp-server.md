---
name: 6sense — connect an agent to the 6sense MCP server
description: Authorize and connect an MCP client to the hosted 6sense remote MCP server, and understand what it can and cannot do before you build on it.
api: mcp/6sense-mcp.yml
operations: []
generated: '2026-08-13'
method: generated
source: mcp/6sense-mcp.yml, well-known/6sense-oauth-authorization-server.json, https://support.6sense.com/docs/set-up-the-6sense-mcp-in-claude
---

# Connect an agent to the 6sense MCP server

6sense runs a **hosted remote MCP server**. There is nothing to install — no npx, no stdio package, no local process. An MCP client connects to a URL and completes an OAuth flow.

## The endpoint

```
https://api.6sense.com/mcp
```

Transport is HTTP. Status is **beta** — beta service terms apply.

## Authorization

Per-user OAuth 2.1. Every user authorizes individually; there is no org-wide service credential and no way to pre-authorize a team.

Discovery is fully standards-compliant, so a conformant MCP client needs no configuration beyond the URL:

1. Client POSTs to `https://api.6sense.com/mcp` without a token.
2. Server returns `401` with
   `WWW-Authenticate: Bearer resource_metadata="https://api.6sense.com/.well-known/oauth-protected-resource/mcp"` (RFC 9728).
3. That document names the resource and the authorization server.
4. `https://api.6sense.com/.well-known/oauth-authorization-server` (RFC 8414) supplies the endpoints.
5. Client registers dynamically (RFC 7591 — `registration_endpoint` is published), runs authorization code + PKCE (`S256`), and requests scope **`mcp:use`**.

`mcp:use` is the only scope. There is no finer grant to ask for.

Both `.well-known` documents are saved verbatim in `well-known/` in this repo.

### Adding it as a custom connector

In Claude: Settings → Connectors → **+ Add custom connector** → name it, paste `https://api.6sense.com/mcp`, Connect, then **Allow access** on the consent screen. 6sense also documents ChatGPT and Microsoft Copilot Studio.

## Entitlement — check this before you build

- The org must have the **Revenue Marketing** platform. Sales Intelligence-only orgs can connect during beta but will get thin data.
- Access is bounded by the authorizing **user's** existing 6sense permissions. Two users on the same connector will see different results, legitimately.

## What it can do

Read-only retrieval over Revvy AI-powered scenarios:

- **Account insights** — what to know about an account before engaging
- **6QA trend analysis** — which accounts became 6sense Qualified and have not been followed up
- **Keyword performance** — where intent moved over a window
- **Ad campaign performance** — spend and engagement by predictive buying stage
- **Website activity** — most engaged accounts by visits
- **Segment discovery** — filter accounts, explore segment membership
- **Market research** — competitors, personas, industry trends, GTM recommendations
- **Product support** — how-to questions about 6sense itself

## What it cannot do

- **No writes.** It does not execute actions or modify data. Do not design a workflow that expects it to.
- **Not the whole data estate.** 6sense states it exposes only Revvy-powered scenarios.
- **Not the REST APIs.** This is the important one: the MCP surface and the public REST APIs are almost disjoint. Record-level contact enrichment, People Search, lead scoring and company firmographics are **REST only** and have no MCP tool. Conversely, 6QA trends, keyword performance and campaign analytics are **MCP only** and have no REST endpoint. See `mcp/6sense-tool-crosswalk.yml`.

If your agent needs to enrich a specific contact or score a specific lead, it needs an API token and the REST APIs — not this connector.

## Verifying the connection

Ask something that can only be answered with 6sense data, e.g. *"Using 6sense, what is the current buying stage and top intent keywords for salesforce.com?"* A working connector invokes a tool and returns account data. A broken one answers from general knowledge or reports no tool available.

A `401` when you open the URL in a browser is **expected** — the endpoint is not browsable and is only meant to be reached by an authenticated MCP client.

## Tool schemas

`tools/list` is OAuth-gated, so the tool names and their `inputSchema`s cannot be read anonymously. Once you have authorized, call `tools/list` and record the real schemas; this repo deliberately does not guess them.
