# Olyx

Olyx is a control plane for production AI. It sits between your application and your model providers — routing requests by policy, recording every decision as a trace, and giving you the data to understand cost, latency, and quality over time.

You keep your provider credentials. Olyx handles routing, observability, and governance.

---

## How it works

<details>
<summary><strong>Using the CLI</strong></summary>

**1. Install**

<details>
<summary>macOS (Apple Silicon)</summary>

```sh
curl -fsSLO https://github.com/Olyx-labs/Olyx-CLI/releases/latest/download/olyx-v0.1.0-aarch64-apple-darwin.tar.gz
tar -xzf olyx-v0.1.0-aarch64-apple-darwin.tar.gz
sudo install -m 0755 olyx /usr/local/bin/olyx
olyx --version
```
</details>

<details>
<summary>macOS (Intel)</summary>

```sh
curl -fsSLO https://github.com/Olyx-labs/Olyx-CLI/releases/latest/download/olyx-v0.1.0-x86_64-apple-darwin.tar.gz
tar -xzf olyx-v0.1.0-x86_64-apple-darwin.tar.gz
sudo install -m 0755 olyx /usr/local/bin/olyx
olyx --version
```
</details>

<details>
<summary>Linux x86_64</summary>

```sh
curl -fsSLO https://github.com/Olyx-labs/Olyx-CLI/releases/latest/download/olyx-v0.1.0-x86_64-unknown-linux-musl.tar.gz
tar -xzf olyx-v0.1.0-x86_64-unknown-linux-musl.tar.gz
sudo install -m 0755 olyx /usr/local/bin/olyx
olyx --version
```
</details>

<details>
<summary>Linux arm64</summary>

```sh
curl -fsSLO https://github.com/Olyx-labs/Olyx-CLI/releases/latest/download/olyx-v0.1.0-aarch64-unknown-linux-musl.tar.gz
tar -xzf olyx-v0.1.0-aarch64-unknown-linux-musl.tar.gz
sudo install -m 0755 olyx /usr/local/bin/olyx
olyx --version
```
</details>

<details>
<summary>Windows (PowerShell)</summary>

```powershell
$version = "v0.1.0"
$asset = "olyx-$version-x86_64-pc-windows-msvc.zip"
Invoke-WebRequest -Uri "https://github.com/Olyx-labs/Olyx-CLI/releases/download/$version/$asset" -OutFile $asset
Expand-Archive $asset -DestinationPath .
Move-Item "olyx-$version-x86_64-pc-windows-msvc\olyx.exe" "$env:LOCALAPPDATA\Microsoft\WindowsApps\olyx.exe"
olyx --version
```
</details>

**2. Configure and run**

```sh
export OLYX_API_KEY=ak_...

# Check your project policy
olyx config

# Open a trace before your model call
olyx trace --metadata '{"service":"checkout","operation":"cart.create","environment":"production"}'

# Make your model call using your own provider credentials
# Provider secrets never leave your environment

# Complete the trace and queue a replay
olyx complete trace_01J6AF...
olyx replay trace_01J6AF...
```

</details>

<details>
<summary><strong>Using the HTTP API</strong></summary>

No install required. Every CLI command maps to an HTTP endpoint.

```sh
export OLYX_API_KEY=ak_...

# Check your project policy
curl https://app.olyxai.io/api/v1/config \
  -H "Authorization: Bearer $OLYX_API_KEY"

# Open a trace before your model call
curl https://app.olyxai.io/api/v1/traces \
  -H "Authorization: Bearer $OLYX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"metadata":{"service":"checkout","operation":"cart.create","environment":"production"}}'
# → {"id":"trace_01J6AF...","status":"pending",...}

# Make your model call using your own provider credentials
# Provider secrets never leave your environment

# Complete the trace
curl -X PATCH https://app.olyxai.io/api/v1/traces/trace_01J6AF.../complete \
  -H "Authorization: Bearer $OLYX_API_KEY"

# Queue a replay
curl https://app.olyxai.io/api/v1/replay \
  -H "Authorization: Bearer $OLYX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"trace_id":"trace_01J6AF..."}'
# → {"job_id":"job_01J6AG...","status":"queued"}
```

</details>

Every completed trace records which model ran, what it cost, how long it took, and whether any policy signals fired. Replay lets you run the same input against a different model to compare before changing production routing.

---

## What's in this org

| Repo | Description |
| :--- | :--- |
| [`Olyx-CLI`](https://github.com/Olyx-labs/Olyx-CLI) | CLI for creating traces, queuing replays, and inspecting project config |

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

Full docs at [app.olyxai.io/docs](https://olyxai.io/docs).

- [Quickstart](https://olyxai.io/docs/v1/guides/quick-start) — first trace in under 5 minutes
- [Authentication](https://olyxai.io/docs/v1/auth) — API keys, project scoping, rotation
- [Routing](https://olyxai.io/docs/v1/guides/routing) — routing tiers, fallbacks, policy simulation
- [Replays](https://olyxai.io/docs/v1/guides/replays) — compare models against historical traffic
- [MCP Integration](https://olyxai.io/docs/v1/guides/mcp) — IDE setup and proxy usage
- [API Reference](https://olyxai.io/docs/v1/api/endpoints) — full endpoint reference

---

**Status:** Closed beta. [Request access →](https://olyxai.io)
