# Olyx

Olyx is a control plane for production AI. It sits between your application and your model providers — routing requests by policy, recording every decision as a trace, and giving you the data to understand cost, latency, and quality over time.

You keep your provider credentials. Olyx handles routing, observability, and governance.

---

## How it works

```sh
# 1. Install the CLI
curl -fsSLO https://github.com/Olyx-labs/Olyx-CLI/releases/latest/download/olyx-linux-x86_64.tar.gz
tar -xzf olyx-linux-x86_64.tar.gz && sudo install olyx /usr/local/bin/olyx

# 2. Configure your project key
export OLYX_API_KEY=ak_...
olyx config

# 3. Open a trace before your model call
olyx trace --metadata '{"service":"checkout","operation":"cart.create","environment":"production"}'

# 4. Make your model call using your own provider credentials
# Provider secrets never leave your environment

# 5. Complete the trace and queue a replay
olyx complete trace_01J6AF...
olyx replay trace_01J6AF...
```

Every completed trace records which model ran, what it cost, how long it took, and whether any policy signals fired. Replay lets you run the same input against a different model to compare before changing production routing.

---

## What's in this org

| Repo | Description |
| :--- | :--- |
| [`Olyx-CLI`](https://github.com/Olyx-labs/Olyx-CLI) | CLI for creating traces, queuing replays, and inspecting project config |
| [`olyx-typescript`](https://github.com/Olyx-labs/olyx-typescript) | TypeScript/Node SDK |
| [`olyx-python`](https://github.com/Olyx-labs/olyx-python) | Python SDK |
| [`olyx-ruby`](https://github.com/Olyx-labs/olyx-ruby) | Ruby SDK |

---

## Core capabilities

**Routing** — Define routing tiers in your project policy. Requests are matched to a model path by cost tier, complexity, or metadata signals. Change routing without touching application code.

**Traces** — Every request that runs through Olyx produces a trace: model selected, tokens used, cost, latency, routing decision, and any guardrail signals. Traces are queryable and replayable.

**Replays** — Re-run a historical trace against a different model or routing configuration. Compare cost and optimization grade before committing a change to production.

**MCP support** — Olyx works as an MCP server (expose `olyx_execute`, `olyx_check`, and `olyx_simulate` to your IDE) and as an MCP proxy (route tool calls from your model through the governed path).

**Governance** — Every routing decision is written to a cryptographically chained ledger. Entries record the selected model, policy rule, cost, and the hash of the previous entry — so modifications are detectable. Weekly exports are available from the dashboard.

**OpenAI-compatible gateway** — Drop Olyx into existing OpenAI-compatible integrations by pointing `base_url` at the Olyx endpoint. No SDK changes required to start collecting traces.

---

## Documentation

Full docs at [app.olyxai.io/docs](https://app.olyxai.io/docs).

- [Quickstart](https://app.olyxai.io/docs/v1/guides/quick-start) — first trace in under 5 minutes
- [Authentication](https://app.olyxai.io/docs/v1/auth) — API keys, project scoping, rotation
- [Routing](https://app.olyxai.io/docs/v1/guides/routing) — routing tiers, fallbacks, policy simulation
- [Replays](https://app.olyxai.io/docs/v1/guides/replays) — compare models against historical traffic
- [MCP Integration](https://app.olyxai.io/docs/v1/guides/mcp) — IDE setup and proxy usage
- [API Reference](https://app.olyxai.io/docs/v1/api/endpoints) — full endpoint reference

---

**Status:** Closed beta. [Request access →](https://app.olyxai.io)
