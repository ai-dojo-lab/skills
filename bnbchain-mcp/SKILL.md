---
name: bnbchain-mcp
description: Use BNB Chain MCP (via mcporter + npx @bnb-chain/mcp@latest) to query BSC/opBNB/EVM chain data, read contracts, and (optionally) send transactions. Read-only works without PRIVATE_KEY; writes require PRIVATE_KEY.
metadata:
  {
    "openclaw": {
      "emoji": "🟡",
      "requires": { "bins": ["mcporter", "node", "npx"] }
    }
  }
---

# BNB Chain MCP (OpenClaw)

This skill makes OpenClaw able to use **BNB Chain MCP** tools through the already-installed `mcporter` CLI.

Source skills repo: https://github.com/bnb-chain/bnbchain-skills (original skill file: `skills/bnbchain-mcp-skill/SKILL.md`).

## Quick test (read-only)

List supported networks:

```bash
mcporter call --stdio "npx -y @bnb-chain/mcp@latest" get_supported_networks --output json
```

Get latest block on BSC:

```bash
mcporter call --stdio "npx -y @bnb-chain/mcp@latest" get_latest_block network=bsc --output json
```

## Read-only vs write

- Read-only tools (blocks/tx/balances/contract reads) do **NOT** need a private key.
- Any state-changing tool needs `PRIVATE_KEY` in the MCP server environment.

### Writes (DON’T paste keys into chat)

Run with an env var locally (example):

```bash
PRIVATE_KEY="..." mcporter call --stdio "npx -y @bnb-chain/mcp@latest" get_address_from_private_key --output json
```

For transfers / contract writes, ALWAYS confirm network + recipient + amount first.

## Notes

- This MCP server is launched via `npx -y @bnb-chain/mcp@latest` each call. If you want faster repeated calls, we can run it as a long-lived daemon and point mcporter at it.
