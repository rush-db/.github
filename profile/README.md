<div align="center">

# RushDB
### The Instant Database for Modern Apps and DS/ML Ops

RushDB is an open-source alternative to Firebase, built on top of Neo4j.

It streamlines application development by automating data normalization, managing relationships, inferring data types automatically, and offering a suite of additional powerful features to accelerate your workflow.

[🌐 Homepage](https://rushdb.com) — [📢 Blog](https://rushdb.com/blog) — [☁️ Platform ](https://app.rushdb.com) — [📖 Docs](https://docs.rushdb.com) — [🧑‍💻 Examples](https://github.com/rush-db/rushdb/examples)
</div>

## 🚀 Feature Highlights

### 1. **No Data Modeling Needed**
Push data of any shape—RushDB handles relationships, data types, and more automatically.

### 2. **Automatic Type Inference**
Minimizes overhead while optimizing performance for high-speed searches.

### 3. **Powerful Search API**
Query data with accuracy using the graph-powered search API.

### 4. **Flexible Data Import**
Easily import data in **JSON**, **CSV**, or **JSONB**, creating data-rich applications fast.

### 5. **Developer-Centric Design**
RushDB prioritizes DX with an intuitive and consistent API.

### 6. **REST API Readiness**
A REST API with SDK-like DX for every operation: manage relationships, create, delete, and search effortlessly.

---

## Usage

1. **Obtain an API Token**:
   - If you’re using **RushDB Cloud**, get your token from [app.rushdb.com](https://app.rushdb.com).
   - For a self-hosted RushDB instance, retrieve the token from the **Dashboard** running locally (`localhost:3000`).

2. **Build Anything**:  
   Easily push, search, and manage relationships within your data.

### With TypeScript / JavaScript

#### Install the SDK

```bash
npm install @rushdb/javascript-sdk
```

#### Push any json data

```typescript
import RushDB from '@rushdb/javascript-sdk';

// Setup SDK
const db = new RushDB("API_TOKEN", {
  // Default URL; only override if necessary.
  url: "https://api.rushdb.com",
});

// Push data: RushDB flattens it into Records and establishes relationships automatically.
await db.records.createMany("COMPANY", {
  name: 'Google LLC',
  address: '1600 Amphitheatre Parkway, Mountain View, CA 94043, USA',
  foundedAt: '1998-09-04T00:00:00.000Z',
  rating: 4.9,
  DEPARTMENT: [{
    name: 'Research & Development',
    description: 'Innovating and creating advanced technologies for AI, cloud computing, and consumer devices.',
    PROJECT: [{
      name: 'Bard AI',
      description: 'A state-of-the-art generative AI model for natural language understanding and creation.',
      active: true,
      budget: 1200000000,
      EMPLOYEE: [{
        name: 'Jeff Dean',
        position: 'Head of AI Research',
        email: 'jeff@google.com',
        dob: '1968-07-16T00:00:00.000Z',
        salary: 3000000,
      }]
    }]
  }]
});
```

#### Find Records by specific criteria
```typescript
// Find Records by specific criteria
const matchedEmployees = await db.records.find({
  labels: ['EMPLOYEE'],
  where: {
    position: { $contains: 'AI' },
    PROJECT: {
      DEPARTMENT: {
        COMPANY: {
          rating: { $gte: 4 },
        },
      },
    },
  },
});

const company = await db.records.findUniq('COMPANY', {
  where: {
    name: 'Google LLC',
  },
});
```

<div align="center">
<b>You Rock</b>  🚀
</div>

---

<div align="center" style="margin-top: 20px">

> Check the [Documentation](https://docs.rushdb.com) and [Examples](https://github.com/rush-db/rushdb/examples) to learn more 🤓

</div>
