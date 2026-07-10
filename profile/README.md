<div align="center">

<img width="160" height="160" alt="Olyx logo" src="https://github.com/user-attachments/assets/6704a659-dd7d-4aa5-8b9b-2d55a127e7f2" />

# Olyx

**Model access, routing, and trace history for production AI apps**

[![Status](https://img.shields.io/badge/Status-Closed%20Beta-orange)](https://olyxai.io)
[![Website](https://img.shields.io/badge/Website-olyxai.io-black)](https://olyxai.io)
[![Access](https://img.shields.io/badge/Access-Request%20Early%20Access-brightgreen)](https://olyxai.io/request-access)

[Website](https://olyxai.io) • [Request Access](https://olyxai.io/request-access) • [Integrations](https://olyxai.io/integrations)

</div>

---

## What Olyx Does

Olyx gives AI teams one control point for model access, routing, traces, cost visibility, and replay.

Start by connecting an existing chat UI such as LibreChat or Open WebUI. Olyx sits between your application and model providers, giving your team a shared model list, request history, cost and latency records, and routing controls without forcing a rewrite of your app.

---

## Core Capabilities

| Capability | Description |
|---|---|
| **Chat UI integration** | Connect tools like LibreChat and Open WebUI through an OpenAI-compatible endpoint. |
| **Model access control** | Expose approved models to apps and teams from one managed layer. |
| **Routing** | Send requests to model paths based on policy, metadata, cost tier, or fallback rules. |
| **Traces** | Record model choice, latency, cost, request metadata, and policy signals for each run. |
| **Replays** | Compare historical traffic against different models or routing settings before changing production behavior. |
| **Governance history** | Keep a decision trail for audits, reviews, debugging, and internal controls. |

---

## Integration Paths

### OpenAI-Compatible Proxy

Point an OpenAI-compatible client at Olyx:

```txt
base_url: https://app.olyxai.io/v1
Existing chat UIs and SDKs can route through Olyx while keeping a familiar OpenAI-style interface.
CLI and Runtime Workflow
Use the CLI to inspect project config, create traces, complete runs, and queue replays:
export OLYX_API_KEY=ak_...
export OLYX_BASE_URL=https://app.olyxai.io

olyx inspect
olyx config
olyx trace --metadata '{"service":"checkout","operation":"cart.create"}'
olyx complete trace_01J6AF...
olyx replay trace_01J6AF...
Public Repositories
Repository	Description	Status
Olyx-CLI	CLI for config inspection, traces, replay, and runtime workflows	Public release planned
Olyx integrations	Guides and examples for LibreChat, Open WebUI, and OpenAI-compatible clients	In progress

Access
Olyx is currently in closed beta.
Request access at olyxai.io/request-access.
