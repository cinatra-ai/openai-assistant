# OpenAI Assistant

A general-purpose conversational assistant for Cinatra, powered by OpenAI models. Chat with it for questions, drafting, analysis, and everyday tasks — it answers through ordinary back-and-forth conversation, asks a clarifying question when a request is ambiguous, and keeps its replies direct and accurate.

**Install.** Add `@cinatra-ai/openai-assistant` from the Cinatra marketplace. The assistant runs on the host runtime and routes model calls to OpenAI. Model credentials are resolved by the platform through the `@cinatra-ai/openai-connector` package — you never supply an API key to this assistant.

**Configuration.** No per-assistant configuration is required. Provider access is administered on the OpenAI connector; this package declares only the assistant persona, its reference skill bundle, and its OpenAI model preference.

## Works with

- OpenAI

## Capabilities

- Hold a natural-language conversation for questions, drafting, and analysis
- Route model calls to OpenAI with credentials resolved through the OpenAI connector
- Load the `chat-assistant-core` skill bundle on every turn
- Run on the Cinatra host runtime with host-runtime turn delivery
