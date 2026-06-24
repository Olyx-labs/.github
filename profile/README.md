# Olyx

Olyx is the control layer for production AI.

It helps teams route model traffic by policy, record every decision as a trace,
and compare cost, latency, and quality before changing production behavior.

You keep your provider credentials. Olyx handles routing, traces, replay, and
governance.

---

## How it works

### CLI pattern

Use the CLI to read project config, create traces, and queue replays while your
application keeps calling the provider directly.

```sh
export OLYX_API_KEY=ak_...
export OLYX_BASE_URL=https://app.olyxai.io

olyx inspect
olyx config
olyx trace --metadata '{"service":"checkout","operation":"cart.create","environment":"production"}'

# make your model call with your own provider credentials

olyx complete trace_01J6AF...
olyx replay trace_01J6AF...
```

### Proxy pattern

If you want Olyx to make the live routing decision in cloud, point your
OpenAI-compatible client at the Olyx endpoint:

```txt
base_url: https://app.olyxai.io/v1
```

Every completed trace records which model ran, what it cost, how long it took,
and whether any policy signals fired. Replay lets you compare outcomes before
changing production routing.

---

## Public repos

=======
Scheduled Release: June 25, 2026
| Repo | Description |
| :--- | :--- |
| [`Olyx-CLI`](https://github.com/Olyx-labs/Olyx-CLI) | Public CLI for project config, traces, replay, and runtime inspection |

---

## Core capabilities

**Routing**
Choose model paths by policy, metadata, cost tier, or safety signals without
rewriting application code.

**Traces**
Record model choice, latency, cost, and security signals for each request.

**Replays**
Run historical traffic against a different model or routing setup before making
a production change.

**Governance**
Keep a chained decision history for audits, reviews, and internal controls.

**OpenAI-compatible endpoint**
Drop Olyx into existing integrations by pointing `base_url` at the Olyx proxy.

---

## Documentation

Docs: [olyxai.io/docs](https://olyxai.io/docs)

- [Quickstart](https://olyxai.io/docs/v1/guides/quick-start)
- [Authentication](https://olyxai.io/docs/v1/auth)
- [Routing](https://olyxai.io/docs/v1/guides/routing)
- [Replays](https://olyxai.io/docs/v1/guides/replays)
- [API Reference](https://olyxai.io/docs/v1/api/endpoints)

---

**Status:** Closed beta. [Request access](https://olyxai.io)
