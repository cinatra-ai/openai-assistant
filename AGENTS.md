# openai-assistant — AGENTS.md

Repository guidance for `@cinatra-ai/openai-assistant`, an `agent`-kind Cinatra extension that declares a provider-chat **assistant** rather than a compiled OpenAgentSpec flow.

## What this repo is

- An assistant declaration, not an OAS agent. The authoritative payload is `cinatra/config.json` → the `assistant` block (validated by `packages/sdk-extensions/src/assistant-declaration.ts` in the cinatra monorepo). There is intentionally no `cinatra/oas.json`.
- Credential-free. Model access and OpenAI keys resolve through `@cinatra-ai/openai-connector` at runtime — declared as a required, runtime, cross-kind `connector` dependency edge in `package.json` → `cinatra.dependencies`. This package handles no secrets.

## Assistant block contract

The `assistant` block is fail-closed (`.strict()` at every level; `formatVersion`/`abiVersion` exactly `1`). Key fields:

- `displayName` `"OpenAI"`, `preferredTag` `"openai"` — a normalized, lowercase flat token (owner ruling 2026-07-22, groganz: all assistant tags are lowercase). Never the tag/handle `chatgpt`.
- `persona` — the provider-chat system identity.
- `skillBundle` `["chat-assistant-core"]` — the reference bundle mounted every turn (lives in its own skill extension; not vendored here).
- `allowedTools` / `allowedAgents` empty; `modelPrefs.provider` `"openai"`; `launch.kind` `"local"`; `delivery.kind` `"host-runtime"`.

## CI

`extension-kind-gate.mjs` runs the self-contained agent-kind gate (manifest shape + dependency-edge shape + README/license). The assistant declaration itself is validated by the monorepo declaration validator at install/registry time. Keep both green.
