<div align="center">

<img width="594" height="603" alt="Olyx-favicon copy" src="https://github.com/user-attachments/assets/6704a659-dd7d-4aa5-8b9b-2d55a127e7f2" />

# Olyx

**The control layer for production AI**

[![Status](https://img.shields.io/badge/Status-Closed%20Beta-orange)](https://olyxai.io)
[![License](https://img.shields.io/badge/License-MIT-blue)](#license)
[![Docs](https://img.shields.io/badge/Docs-olyxai.io-blueviolet)](https://olyxai.io/docs)

[Website](https://olyxai.io) • [Documentation](https://olyxai.io/docs) • [Request Access](https://olyxai.io)

</div>

---

## Overview

Olyx helps teams **route model traffic by policy**, **record every decision as a trace**, and **compare cost, latency, and quality** before changing production behavior.

- **Keep your provider credentials** — Olyx doesn't store sensitive data
- **Handle routing, traces, replay, and governance** — All in one platform
- **Production-ready** — Built for enterprise AI workflows

---

## ✨ Core Capabilities

| Capability | Description |
|---|---|
| **🛣️ Routing** | Choose model paths by policy, metadata, cost tier, or safety signals without rewriting application code. |
| **📊 Traces** | Record model choice, latency, cost, and security signals for each request. |
| **🔄 Replays** | Run historical traffic against a different model or routing setup before making production changes. |
| **🔐 Governance** | Keep a chained decision history for audits, reviews, and internal controls. |
| **🔌 OpenAI-compatible** | Drop Olyx into existing integrations by pointing `base_url` at the Olyx proxy. |

---

## 🚀 Quick Start

### CLI Pattern

Use the CLI to read project config, create traces, and queue replays:

```bash
export OLYX_API_KEY=ak_...
export OLYX_BASE_URL=https://app.olyxai.io

olyx inspect
olyx config
olyx trace --metadata '{"service":"checkout","operation":"cart.create","environment":"production"}'

# Make your model call with your own provider credentials

olyx complete trace_01J6AF...
olyx replay trace_01J6AF...
```

### Proxy Pattern

Point your OpenAI-compatible client at the Olyx endpoint:

```
base_url: https://app.olyxai.io/v1
```

Every completed trace records which model ran, what it cost, how long it took, and whether any policy signals fired. Replay lets you compare outcomes before changing production routing.

---

## 📦 Tech Stack

<div align="center">

| Category | Technologies |
|---|---|
| **Frontend** | TypeScript (25.8%), Astro (14.7%), JavaScript (3.1%) |
| **Backend** | Ruby (43.4%), TypeScript (25.8%) |
| **Content** | MDX (9.5%) |
| **Styling** | CSS (2.5%) |

</div>

---

## 📚 Public Repositories

| Repository | Description | Release |
|---|---|---|
| [`Olyx-CLI`](https://github.com/Olyx-labs/Olyx-CLI) | Public CLI for project config, traces, replay, and runtime inspection | July 20, 2026 |

---

## 📖 Documentation

Explore our comprehensive docs at **[olyxai.io/docs](https://olyxai.io/docs)**

- 🎯 [Quickstart](https://olyxai.io/docs/v1/guides/quick-start)
- 🔑 [Authentication](https://olyxai.io/docs/v1/auth)
- 🛣️ [Routing](https://olyxai.io/docs/v1/guides/routing)
- 🔄 [Replays](https://olyxai.io/docs/v1/guides/replays)
- 📡 [API Reference](https://olyxai.io/docs/v1/api/endpoints)

---

## 🤝 Contributing

We're currently in closed beta. [Request access](https://olyxai.io) to get started.

---

## 📄 License

This project is licensed under the MIT License — see LICENSE file for details.

---

<div align="center">

**Status:** Closed Beta — [Join the waitlist](https://olyxai.io)

Made with ❤️ by [Olyx Labs](https://olyxai.io)

</div>
