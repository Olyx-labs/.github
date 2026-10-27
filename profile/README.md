<div align="center">

<img width="160" height="160" alt="Olyx logo" src="https://github.com/user-attachments/assets/6704a659-dd7d-4aa5-8b9b-2d55a127e7f2" />

# Olyx Labs

**Tools for connecting, inspecting, and protecting AI applications.**

[Website](https://olyxai.io) · [Documentation](https://docs.olyxai.io) · [Articles](https://olyxai.io/articles)

</div>

We build Olyx CLI and Olyx Guardrails. Use the CLI to send model requests,
inspect failures, and compare responses. Use Guardrails to check the content
entering or leaving a Ruby application. Each works on its own.

## Olyx CLI

Olyx CLI connects to a hosted endpoint, a model server on your own machine,
or a provider plugin. Give models explicit aliases, configure ordered fallbacks,
and stream responses. Requests and responses are recorded in a local SQLite
database so you can inspect a trace or replay it against another model.

- **Route:** choose a configured model alias and try fallbacks in order.
- **Inspect:** see saved inputs, outputs, provider attempts, errors, and latency.
- **Replay:** send a recorded request again or compare models while keeping the original trace.
- **Serve:** connect an application through OpenAI-compatible chat, embeddings, and model-list endpoints.
- **Extend:** write a provider adapter without changing the CLI.

The CLI runs on your machine or infrastructure. Model requests go to the
endpoint you configure. No Olyx account is required. Your application owns
agent orchestration, tool execution, document ingestion, and retrieval.

Run it with Node.js 22 or newer:

```sh
npx olyx-cli --help
```

A global npm installation provides the short `oy` command. Rust and a database
server are not required. A local model needs a running inference server;
hosted services may require credentials and charge for usage.

[Source](https://github.com/Olyx-labs/Olyx-CLI) · [Quickstart](https://docs.olyxai.io/getting-started/quickstart/) · [Provider plugins](https://docs.olyxai.io/guides/plugins/)

## Olyx Guardrails

**Lightweight input and output checks for Ruby and Rails.**

Use configurable policies to detect prompt injection, personal information,
secrets, and restricted content. Get an allow/block decision or redact recognized
content at the boundaries your application chooses.

Deterministic checks run locally. Guardrails works without the CLI or an Olyx
account. Rails is optional; an optional model-based check uses the adapter you
provide.

Add the gem to your application's `Gemfile`:

```ruby
gem "olyx-guardrails", "~> 1.2"
```

```sh
bundle install
```

Requires Ruby 3.4 or newer.

[Source](https://github.com/Olyx-labs/olyx-guardrails) · [Quickstart](https://docs.olyxai.io/guardrails/quickstart/) · [RubyGems](https://rubygems.org/gems/olyx-guardrails)

## Questions and contributions

Start with the documentation for the project you use. Report bugs and suggest
improvements in that project's GitHub issues. For development setup and security
reports, see its contributing guide and security policy.

Both projects use the Apache License 2.0. See each repository for its license
and notices.
