<div align="center">

![RushDB Logo](https://raw.githubusercontent.com/rush-db/rushdb/main/rushdb-logo.svg)

# RushDB

### The memory layer for AI agents and apps.

Durable agent memory, semantic search, and graph relationships through one API.
Push JSON once; query it by meaning, structure, or connection.

[![GitHub Stars](https://img.shields.io/github/stars/rush-db/rushdb?style=social)](https://github.com/rush-db/rushdb)
[![TypeScript SDK](https://img.shields.io/npm/v/%40rushdb%2Fjavascript-sdk?label=TypeScript)](https://www.npmjs.com/package/@rushdb/javascript-sdk)
[![Python SDK](https://img.shields.io/pypi/v/rushdb?label=Python)](https://pypi.org/project/rushdb/)
[![OpenClaw Memory](https://img.shields.io/npm/v/%40rushdb%2Fopenclaw-memory?label=OpenClaw)](https://www.npmjs.com/package/@rushdb/openclaw-memory)
[![Hermes Memory](https://img.shields.io/pypi/v/rushdb-hermes-memory?label=Hermes)](https://pypi.org/project/rushdb-hermes-memory/)

[Website](https://rushdb.com) • [Documentation](https://docs.rushdb.com) • [Cloud](https://app.rushdb.com) • [Agent setup](https://rushdb.com/agent-setup) • [Examples](https://github.com/rush-db/examples)

</div>

---

## Give your agent the right kind of memory

RushDB supports automatic runtime memory, model-directed tools, and application-controlled memory without forcing them into one abstraction.

| What you need                                                      | Use                                                                                                                                                                      |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Automatic recall and completed-turn persistence in OpenClaw        | [`@rushdb/openclaw-memory`](https://github.com/rush-db/rushdb-openclaw-memory)                                                                                           |
| Native lifecycle memory in Hermes Agent                            | [`rushdb-hermes-memory`](https://github.com/rush-db/rushdb-hermes-memory)                                                                                                |
| Explicit graph queries and intentional memory writes from an agent | [`@rushdb/mcp-server`](https://www.npmjs.com/package/@rushdb/mcp-server)                                                                                                 |
| Reusable modeling, query, and memory guidance for coding agents    | [RushDB Agent Skills](https://github.com/rush-db/rushdb/tree/main/packages/skills)                                                                                       |
| Application-controlled agent lifecycle                             | [`@rushdb/agent-memory-contract`](https://www.npmjs.com/package/@rushdb/agent-memory-contract) with a RushDB SDK                                                         |
| Records, relationships, semantic search, and application data      | [TypeScript](https://www.npmjs.com/package/@rushdb/javascript-sdk), [Python](https://pypi.org/project/rushdb/), or [REST](https://docs.rushdb.com/rest-api/introduction) |

Native memory owns automatic recall and completed-turn capture. MCP remains the explicit knowledge plane for records such as `DECISION`, `TASK`, `ENTITY`, and `ARTIFACT`, so the same turn is not written twice.

## Native memory for OpenClaw and Hermes

### OpenClaw

```bash
openclaw plugins install @rushdb/openclaw-memory
export RUSHDB_API_KEY="your-project-api-key"
```

The additive plugin recalls before prompt construction and durably captures successful completed turns while leaving OpenClaw's Markdown and SQLite memory active.

[OpenClaw setup and behavior →](https://docs.rushdb.com/connect/openclaw-memory)

### Hermes Agent

```bash
pip install rushdb-hermes-memory
export RUSHDB_API_KEY="your-project-api-key"
hermes memory setup
```

The native `MemoryProvider` participates in prefetch, completed-turn sync, pre-compression, session changes, session end, and shutdown. Supported explicit Hermes memory writes become scoped memory facts.

[Hermes setup and behavior →](https://docs.rushdb.com/connect/hermes-memory)

Both connectors:

- apply trusted agent, profile, privacy, participant, and sandbox scope before semantic ranking;
- capture bounded user/assistant content instead of complete transcripts or tool output;
- fail open when remote recall is slow or unavailable;
- write through a local durable outbox and replay after restart;
- use deterministic identities and idempotent RushDB upserts;
- keep a recent-write fallback while managed embeddings become visible.

## One event contract across runtimes

[`AgentMemoryEvent v1`](https://docs.rushdb.com/learn/agent-memory/event-contract) gives native connectors and custom harnesses the same provider-neutral memory model.

| Record        | Purpose                                             | Semantic property |
| ------------- | --------------------------------------------------- | ----------------- |
| `EPISODE`     | One bounded completed turn or lifecycle observation | `summary`         |
| `MEMORY_FACT` | A curated preference, rule, or fact                 | `text`            |

The `@rushdb/agent-memory-contract` package publishes TypeScript primitives, deterministic identity helpers, the JSON Schema, and a language-neutral conformance fixture.

```bash
pnpm add @rushdb/agent-memory-contract
```

## Connect any MCP client

For ChatGPT, Claude.ai, and other remote clients, connect directly to:

```text
https://mcp.rushdb.com/mcp
```

For local MCP clients such as Claude Desktop, Cursor, Windsurf, and VS Code:

```json
{
  "mcpServers": {
    "rushdb": {
      "command": "npx",
      "args": ["@rushdb/mcp-server"],
      "env": {
        "RUSHDB_API_KEY": "your-project-api-key"
      }
    }
  }
}
```

[MCP installation and OAuth setup →](https://docs.rushdb.com/connect/mcp)

## Build memory into your own agent

Get an API key at [app.rushdb.com](https://app.rushdb.com), then install a RushDB SDK:

```bash
pnpm add @rushdb/javascript-sdk
# or
pip install rushdb
```

```typescript
import RushDB from '@rushdb/javascript-sdk'

const db = new RushDB('RUSHDB_API_KEY')

await db.ai.indexes.create({
  label: 'MEMORY',
  propertyName: 'text'
})

await db.records.create({
  label: 'MEMORY',
  data: {
    agentId: 'agent-42',
    topic: 'authentication',
    text: 'Use passkeys for the new account flow.'
  }
})

const memories = await db.records.vectorSearch({
  labels: ['MEMORY'],
  propertyName: 'text',
  query: 'What did we decide about authentication?',
  where: { agentId: 'agent-42' },
  limit: 10
})
```

RushDB manages embeddings server-side. The same query can combine semantic ranking with structured filters and graph traversal.

## Why RushDB

| Without RushDB                                  | With RushDB                                          |
| ----------------------------------------------- | ---------------------------------------------------- |
| Separate vector, graph, and application stores  | One graph + vector API                               |
| Manual embedding pipeline                       | Managed embeddings on every indexed write            |
| Schema and migration work before ingestion      | Push arbitrary nested JSON                           |
| Relationships reconstructed in application code | Native traversal and relationship discovery          |
| Runtime-specific memory formats                 | Shared event contract for native and custom adapters |

You also get filtering, aggregation, transactions, CSV and JSON import, cloud and self-hosted deployment, TypeScript and Python SDKs, REST, MCP, and agent skills.

## Repositories

| Project                                                                     | What it contains                                                                                  |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [rushdb](https://github.com/rush-db/rushdb)                                 | Core API, dashboard, TypeScript SDK, MCP server, agent contract, skills, and deployment templates |
| [rushdb-python](https://github.com/rush-db/rushdb-python)                   | Python SDK                                                                                        |
| [rushdb-openclaw-memory](https://github.com/rush-db/rushdb-openclaw-memory) | Additive OpenClaw native memory plugin                                                            |
| [rushdb-hermes-memory](https://github.com/rush-db/rushdb-hermes-memory)     | Hermes Agent native memory provider                                                               |
| [docs](https://github.com/rush-db/docs)                                     | Source for [docs.rushdb.com](https://docs.rushdb.com)                                             |
| [examples](https://github.com/rush-db/examples)                             | Runnable integrations and use cases                                                               |

## Start here

| Topic                         | Link                                                                             |
| ----------------------------- | -------------------------------------------------------------------------------- |
| Give an agent the setup guide | [rushdb.com/agent-setup](https://rushdb.com/agent-setup)                         |
| Agent integrations            | [Connect agents](https://docs.rushdb.com/connect/agents)                         |
| Agent skills                  | [Install RushDB skills](https://docs.rushdb.com/connect/skills)                  |
| Agent memory quickstart       | [Build persistent memory](https://docs.rushdb.com/learn/agent-memory/quickstart) |
| TypeScript SDK                | [SDK documentation](https://docs.rushdb.com/typescript-sdk/introduction)         |
| Python SDK                    | [SDK documentation](https://docs.rushdb.com/python-sdk/introduction)             |
| Self-hosting                  | [Deployment guide](https://docs.rushdb.com/deploy/local-hosting)                 |

<div align="center">

**[Create a free RushDB project →](https://app.rushdb.com)**

[Open an issue](https://github.com/rush-db/rushdb/issues) • [Start a discussion](https://github.com/orgs/rush-db/discussions) • [hi@rushdb.com](mailto:hi@rushdb.com)

</div>
