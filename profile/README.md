<div align="center">

![RushDB Logo](https://raw.githubusercontent.com/rush-db/rushdb/main/rushdb-logo.svg)

# RushDB

### The memory layer for AI agents and apps.

Push any JSON. Get graph relationships and vector search automatically.
No schema. No pipeline. No glue code.

[![GitHub Stars](https://img.shields.io/github/stars/rush-db/rushdb?style=social)](https://github.com/rush-db/rushdb)
[![Follow on X](https://img.shields.io/twitter/follow/rushdb?style=social)](https://x.com/RushDatabase)
[![NPM Version](https://img.shields.io/npm/v/%40rushdb%2Fjavascript-sdk?label=npm)](https://www.npmjs.com/package/@rushdb/javascript-sdk)
[![PyPI Version](https://img.shields.io/pypi/v/rushdb?label=pypi)](https://pypi.org/project/rushdb/)

[Website](https://rushdb.com) • [Documentation](https://docs.rushdb.com) • [Cloud](https://app.rushdb.com) • [Examples](https://github.com/rush-db/examples)

</div>

---

## The problem

AI applications usually end up with multiple databases and a lot of glue code:
one for key-value memory, one for vectors, one for relationships.

RushDB replaces that with one API. Push JSON once. Query with graph traversal,
semantic search, or both in one call.

| Without RushDB                           | With RushDB                       |
| ---------------------------------------- | --------------------------------- |
| Redis + vector DB + graph DB + glue code | One API                           |
| Schema design and migration churn        | Push any JSON, no schema required |
| Separate embedding pipeline              | Managed embeddings, server-side   |
| Manual relationship modeling             | Auto-detected relationships       |

---

## Quick start

Get an API key at [app.rushdb.com](https://app.rushdb.com), then:

```bash
npm install @rushdb/javascript-sdk
# or
pip install rushdb
```

```typescript
import RushDB from '@rushdb/javascript-sdk'

const db = new RushDB('RUSHDB_API_KEY')

await db.ai.indexes.create({ label: 'MEMORY', propertyName: 'output' })

await db.records.create({
  label: 'MEMORY',
  data: {
    agent_id: 'agent-42',
    topic: 'Q4 results',
    output: summaryText
  }
})

const memories = await db.ai.search({
  labels: ['MEMORY'],
  propertyName: 'output',
  query: 'what did we decide about Q4?',
  where: { agent_id: 'agent-42' },
  limit: 10
})
```

---

## What you get

- Managed embeddings and semantic search
- Graph and vector in one query
- Zero-schema JSON ingestion
- Unified query API for traversal, filtering, and aggregation
- MCP server support for agent tooling
- Cloud and self-hosted deployment options

---

## Core repositories

| Project         | Link                                                            |
| --------------- | --------------------------------------------------------------- |
| RushDB Platform | https://github.com/rush-db/rushdb                               |
| TypeScript SDK  | https://www.npmjs.com/package/@rushdb/javascript-sdk            |
| Python SDK      | https://pypi.org/project/rushdb/                                |
| MCP Server      | https://github.com/rush-db/rushdb/tree/main/packages/mcp-server |
| Agent Skills    | https://github.com/rush-db/rushdb/tree/main/packages/skills     |
| Examples        | https://github.com/rush-db/examples                             |

---

## Learn more

| Topic          | Link                                                |
| -------------- | --------------------------------------------------- |
| Quick Tutorial | https://docs.rushdb.com/get-started/quick-tutorial  |
| TypeScript SDK | https://docs.rushdb.com/typescript-sdk/introduction |
| Python SDK     | https://docs.rushdb.com/python-sdk/introduction     |
| REST API       | https://docs.rushdb.com/rest-api/introduction       |
| MCP Server     | https://docs.rushdb.com/mcp-server/introduction     |

<div align="center">

Need something not supported yet? Open an issue or start a discussion.

</div>
