# VaultVision MCP

Public connection metadata and usage notes for the VaultVision read-only
Hyperliquid vault research server.

- MCP endpoint: <https://vaultvision.tech/mcp>
- Official MCP Registry: <https://registry.modelcontextprotocol.io/v0.1/servers?search=io.github.0xkayser/vaultvision>
- Setup and tool reference: <https://vaultvision.tech/developers#agents>
- Live scanner: <https://vaultvision.tech/vaults/scanner>
- OpenAPI contract: <https://vaultvision.tech/openapi.json>

VaultVision is an independent analytics product. It is not affiliated with
Hyperliquid.

## What agents can do

The remote server exposes nine read-only tools:

- `search` and `fetch` for VaultVision's public research surface
- `search_vaults` and `get_vault` for current vault evidence
- `rank_vaults` and `compare_vaults` for bounded comparisons
- `explain_vault_risk` for model inputs and caveats
- `get_hlp_metrics` for current HLP evidence
- `get_recent_alerts` for retained research alerts

Responses include timestamps, source labels, canonical VaultVision links, and
risk caveats. APR, returns, rank, risk, entry quality, deposit status, and
alerts can change.

## What agents cannot do

The server cannot:

- connect a wallet or request a signature;
- place or copy a trade;
- submit a vault deposit or withdrawal;
- move funds or take custody;
- guarantee a return or provide personalized investment advice.

## Connect

Use this Streamable HTTP URL in a compatible MCP client:

```text
https://vaultvision.tech/mcp
```

Claude Pro and Max users can add it under **Customize -> Connectors -> Add
custom connector**. Team and Enterprise owners can add the same URL under
**Organization settings -> Connectors**.

For other clients, create a remote MCP connection named `VaultVision` with the
URL above. The server is public and does not require credentials.

The published Registry identifier is `io.github.0xkayser/vaultvision`. The
Registry entry is released from this repository through GitHub Actions using
OIDC, so no long-lived registry token is stored in the repository.

## Verify the server

Discover the current protocol contract:

```bash
curl -s https://vaultvision.tech/mcp \
  -H 'Content-Type: application/json' \
  -H 'MCP-Protocol-Version: 2026-07-28' \
  -d '{"jsonrpc":"2.0","id":1,"method":"server/discover","params":{}}'
```

List tools:

```bash
curl -s https://vaultvision.tech/mcp \
  -H 'Content-Type: application/json' \
  -d '{"jsonrpc":"2.0","id":2,"method":"tools/list","params":{}}'
```

## Evidence contract

When quoting or republishing results:

1. Keep the checked timestamp and row-level data timestamps.
2. Preserve source labels and the canonical VaultVision URL.
3. State that risk and entry fields are VaultVision models.
4. Revalidate fast-changing values before a capital decision.
5. Do not turn a ranking into a deposit recommendation.

## Policies and support

- Privacy: <https://vaultvision.tech/privacy>
- Terms: <https://vaultvision.tech/terms>
- Support: <https://vaultvision.tech/support>
- Security reports: <mailto:security@vaultvision.tech>

This repository intentionally contains public connection metadata and
documentation only. The VaultVision application repository remains private.
