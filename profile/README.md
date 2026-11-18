<div align="center">

<img src="https://raw.githubusercontent.com/rush-db/rushdb/main/rushdb-logo.svg" alt="RushDB logo" width="96">

# RushDB

<sub>The database for AI</sub>

**Graph, vector and analytics on the same records. Every write keeps a live schema of labels, fields and values, so agents query real fields instead of guessing.**

[![GitHub Stars](https://img.shields.io/github/stars/rush-db/rushdb?style=social)](https://github.com/rush-db/rushdb)
[![JavaScript SDK](https://img.shields.io/npm/v/%40rushdb%2Fjavascript-sdk?label=JavaScript%20SDK)](https://www.npmjs.com/package/@rushdb/javascript-sdk)
[![Python SDK](https://img.shields.io/pypi/v/rushdb?label=Python%20SDK)](https://pypi.org/project/rushdb/)
[![MCP server](https://img.shields.io/npm/v/%40rushdb%2Fmcp-server?label=MCP%20server)](https://www.npmjs.com/package/@rushdb/mcp-server)

[Website](https://rushdb.com) • [Docs](https://docs.rushdb.com) • [RushDB Cloud](https://app.rushdb.com) • [Examples](https://github.com/rush-db/examples) • [Discussions](https://github.com/orgs/rush-db/discussions)

</div>

---

Bring data in the way you have it: nested JSON, CSV, SQL, Cypher or Mongo-style writes, or change streams from your databases. RushDB stores it as typed records linked into a graph and answers relationship queries, vector and full-text search, and aggregations from those same records, over HTTP, the PostgreSQL wire protocol, Bolt, gRPC or MCP. One Rust binary, Apache-2.0, or managed on RushDB Cloud.

## Get started

1. Start a local database:

   ```bash
   curl -fsSL https://rushdb.com/install.sh | sh
   mkdir my-app && cd my-app && ~/.rushdb/bin/rushdb up
   ```

   Or `brew install rush-db/tap/rushdb`, or Docker:

   ```bash
   docker run -p 127.0.0.1:3000:3000 -v rushdb:/data -e RUSHDB_TOKEN=change-me rushdb/rushdb:3
   ```

2. Add an SDK, `npm install @rushdb/javascript-sdk` or `pip install rushdb`, and follow the [quickstart](https://github.com/rush-db/rushdb#quickstart).
3. Working with an agent? Hand it [rushdb.com/agent-setup](https://rushdb.com/agent-setup), or add the [MCP server](https://github.com/rush-db/mcp-server).
4. Prefer managed? Sign up for [RushDB Cloud](https://app.rushdb.com).

## Repositories

| | |
|---|---|
| **Core** | [rushdb](https://github.com/rush-db/rushdb) (the database) · [docs](https://github.com/rush-db/docs) · [examples](https://github.com/rush-db/examples) |
| **SDKs** | [javascript-sdk](https://github.com/rush-db/javascript-sdk) · [rushdb-python](https://github.com/rush-db/rushdb-python) |
| **Agents** | [mcp-server](https://github.com/rush-db/mcp-server) · [skills](https://github.com/rush-db/skills) · [agent-plugins](https://github.com/rush-db/agent-plugins) · [agent-memory-contract](https://github.com/rush-db/agent-memory-contract) · [rushdb-openclaw-memory](https://github.com/rush-db/rushdb-openclaw-memory) · [rushdb-hermes-memory](https://github.com/rush-db/rushdb-hermes-memory) |
| **Frameworks** | [langchain-rushdb](https://github.com/rush-db/langchain-rushdb) (LangChain, LangGraph) · [llama-index-rushdb](https://github.com/rush-db/llama-index-rushdb) |
| **Data in** | [connectors](https://github.com/rush-db/connectors) · [debezium-server-rushdb](https://github.com/rush-db/debezium-server-rushdb) · [obsidian-plugin](https://github.com/rush-db/obsidian-plugin) |

**RushDB 2.x (legacy)**, the Neo4j-based stack, lives on the [`2.x` branch of rush-db/rushdb](https://github.com/rush-db/rushdb/tree/2.x) with security fixes until 2027-10-28.

<div align="center">

[Open an issue](https://github.com/rush-db/rushdb/issues) • [Start a discussion](https://github.com/orgs/rush-db/discussions) • [hi@rushdb.com](mailto:hi@rushdb.com)

</div>
