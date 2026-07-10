<div align="center">

<img width="160" height="160" alt="Olyx logo" src="https://github.com/user-attachments/assets/6704a659-dd7d-4aa5-8b9b-2d55a127e7f2" />

# Olyx

**A model access layer for AI apps and chat UIs**

[Website](https://olyxai.io) · [Request Access](https://olyxai.io/request-access) · [Integrations](https://olyxai.io/integrations) | https://olyxhq.slack.com/join/shared_invite/zt-42n7g24g0-0anZo~uDC_STGpoBu47SyA#/shared-invite/email

</div>

---

## How Olyx Works

Olyx sits between your AI app and model providers, giving teams one place to manage model access, routing, traces, cost, and replay.

Connect an existing chat UI such as LibreChat or Open WebUI through an OpenAI-compatible endpoint. Your app keeps the same client shape, while Olyx records which model ran, how long it took, what it cost, and which routing or policy decision was applied.

Use Olyx to start with chatbots, then grow into a shared model access layer for production AI systems.

It supports two integration paths: a proxy pattern for OpenAI-compatible clients, and a CLI/runtime pattern for apps that call providers directly.

If Olyx cannot observe or reproduce a run, it does not pretend to manage it.

[→ Request access](https://olyxai.io/request-access)

---

## What Olyx Helps With

| Capability | What it does |
|---|---|
| **Chat UI integration** | Connect LibreChat, Open WebUI, and OpenAI-compatible tools through one model endpoint. |
| **Model access** | Expose approved models to teams and apps without scattering provider credentials. |
| **Routing** | Route requests by model tier, metadata, fallback rules, or cost controls. |
| **Traces** | Record model choice, latency, cost, metadata, and policy signals for each request. |
| **Replay** | Compare past traffic against a different model or routing setup before changing production behavior. |
| **Decision history** | Keep a clear record of model decisions for debugging, reviews, and audits. |

---

## Get Started

Olyx is currently in closed beta.

- Request access: [olyxai.io/request-access](https://olyxai.io/request-access)
- Connect LibreChat: [LibreChat integration](https://olyxai.io/integrations/librechat)
- Connect Open WebUI: [Open WebUI integration](https://olyxai.io/integrations/open-webui)
- Public CLI: [`Olyx-CLI`](https://github.com/Olyx-labs/Olyx-CLI)

---

## About Olyx Labs

Olyx Labs builds infrastructure for teams running AI systems in production.

Olyx is our model access layer: a practical control point for chat UIs, internal tools, and production apps that need shared model access, routing, trace history, cost visibility, and safer rollout workflows.

[→ olyxai.io](https://olyxai.io)
