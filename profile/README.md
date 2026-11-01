<div align="center">

![RushDB Logo](https://raw.githubusercontent.com/rush-db/rushdb/main/rushdb-logo.svg)

# RushDB — the open-source database for AI

### One database for your records, their relationships, and search over them.

[![GitHub Stars](https://img.shields.io/github/stars/rush-db/rushdb?style=social)](https://github.com/rush-db/rushdb)
[![JavaScript SDK](https://img.shields.io/npm/v/%40rushdb%2Fjavascript-sdk?label=JavaScript%20SDK)](https://www.npmjs.com/package/@rushdb/javascript-sdk)
[![Python SDK](https://img.shields.io/pypi/v/rushdb?label=Python%20SDK)](https://pypi.org/project/rushdb/)
[![MCP server](https://img.shields.io/npm/v/%40rushdb%2Fmcp-server?label=MCP%20server)](https://www.npmjs.com/package/@rushdb/mcp-server)
[![OpenClaw](https://img.shields.io/npm/v/%40rushdb%2Fopenclaw-memory?label=OpenClaw)](https://www.npmjs.com/package/@rushdb/openclaw-memory)
[![Hermes](https://img.shields.io/pypi/v/rushdb-hermes-memory?label=Hermes)](https://pypi.org/project/rushdb-hermes-memory/)

[Website](https://rushdb.com) • [Documentation](https://docs.rushdb.com) • [RushDB Cloud](https://app.rushdb.com) • [Examples](https://github.com/rush-db/examples)

</div>

---

Write JSON. RushDB infers the types, links nested objects into a graph, and keeps a schema catalog that is updated on every write. Query it with its JSON query language, SQL, Cypher, GQL, Gremlin, SQL/PGQ or Mongo-style documents, plus vector, full-text and hybrid search, over HTTP, the Postgres wire protocol, Bolt, gRPC or MCP. One Rust binary, Apache-2.0, or managed on RushDB Cloud.

## Install

```bash
curl -fsSL https://rushdb.com/install.sh | sh && rushdb up
brew install rush-db/tap/rushdb
docker run -p 3000:3000 -e RUSHDB_TOKEN=change-me rushdb/rushdb:3
```

## Agent memory

Agent memory is one use case: memories are records with relationships, filtered by scope and ranked by meaning. Give your agent the setup guide at [rushdb.com/agent-setup](https://rushdb.com/agent-setup), or pick a package:

| What you need | Use |
|---|---|
| Automatic recall and completed-turn persistence in OpenClaw | [`rushdb-openclaw-memory`](https://github.com/rush-db/rushdb-openclaw-memory) |
| Native lifecycle memory in Hermes Agent | [`rushdb-hermes-memory`](https://github.com/rush-db/rushdb-hermes-memory) |
| One provider-neutral memory event contract for your own harness | [`agent-memory-contract`](https://github.com/rush-db/agent-memory-contract) |
| Explicit queries and memory writes from any MCP client | [`@rushdb/mcp-server`](https://github.com/rush-db/mcp-server) |
| Querying, data modeling and agent memory guidance for coding agents | [RushDB agent skills](https://github.com/rush-db/skills) |

The OpenClaw and Hermes providers apply agent, profile and privacy scope before ranking, capture bounded user and assistant content rather than full transcripts, write through a local outbox that replays after a restart, and keep working when recall is slow or unavailable.

## Repositories

| Project | What it contains |
|---|---|
| [rushdb](https://github.com/rush-db/rushdb) | RushDB: the `rushdb` server and CLI |
| [javascript-sdk](https://github.com/rush-db/javascript-sdk) | RushDB SDK for JavaScript and TypeScript |
| [rushdb-python](https://github.com/rush-db/rushdb-python) | RushDB SDK for Python |
| [mcp-server](https://github.com/rush-db/mcp-server) | MCP server for RushDB |
| [docs](https://github.com/rush-db/docs) | Source for [docs.rushdb.com](https://docs.rushdb.com) |
| [examples](https://github.com/rush-db/examples) | Runnable examples; `3.x/` is current |

**RushDB 2.x (legacy)**, the Neo4j-based TypeScript stack, lives on the [`2.x` branch of rush-db/rushdb](https://github.com/rush-db/rushdb/tree/2.x) and the `rushdb/platform` image. It gets security fixes only until 2027-10-28.

<div align="center">

[Open an issue](https://github.com/rush-db/rushdb/issues) • [Start a discussion](https://github.com/orgs/rush-db/discussions) • [hi@rushdb.com](mailto:hi@rushdb.com)

</div>
