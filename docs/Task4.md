# Diagrams

Material for MkDocs renders [Mermaid.js](https://mermaid.js.org/) diagrams natively.
Write diagrams as fenced code blocks — no plugins or image exports needed.

## Configuration

```yaml
markdown_extensions:
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
```

---

## Flowchart

Use flowcharts to illustrate processes, decision trees, and request lifecycles.

````markdown
```mermaid
flowchart LR
  A[Client] --> B{Auth?}
  B -- Yes --> C[API Server]
  B -- No  --> D[401 Unauthorized]
  C --> E[(Database)]
  C --> F[200 Response]
```
````

**Result:**

```mermaid
flowchart LR
  A[Client] --> B{Auth?}
  B -- Yes --> C[API Server]
  B -- No  --> D[401 Unauthorized]
  C --> E[(Database)]
  C --> F[200 Response]
```

---

## Sequence Diagram

Sequence diagrams show message exchanges between actors over time —
perfect for documenting authentication flows and API handshakes.

````markdown
```mermaid
sequenceDiagram
  autonumber
  participant C as Client
  participant A as Auth Service
  participant S as API Server

  C->>A: POST /oauth/token
  A-->>C: access_token
  C->>S: GET /v1/data (Bearer token)
  S->>A: Validate token
  A-->>S: Token valid
  S-->>C: 200 OK { data }
```
````

**Result:**

```mermaid
sequenceDiagram
  autonumber
  participant C as Client
  participant A as Auth Service
  participant S as API Server

  C->>A: POST /oauth/token
  A-->>C: access_token
  C->>S: GET /v1/data (Bearer token)
  S->>A: Validate token
  A-->>S: Token valid
  S-->>C: 200 OK { data }
```

---

## Entity Relationship Diagram

Use ERDs to document data models and database schemas.

````markdown
```mermaid
erDiagram
  USER {
    uuid   id PK
    string email
    string name
  }
  COLLECTION {
    uuid   id PK
    uuid   owner_id FK
    string name
  }
  REQUEST {
    uuid   id PK
    uuid   collection_id FK
    string method
    string url
  }

  USER        ||--o{ COLLECTION : owns
  COLLECTION  ||--o{ REQUEST    : contains
```
````

**Result:**

```mermaid
erDiagram
  USER {
    uuid   id PK
    string email
    string name
  }
  COLLECTION {
    uuid   id PK
    uuid   owner_id FK
    string name
  }
  REQUEST {
    uuid   id PK
    uuid   collection_id FK
    string method
    string url
  }

  USER        ||--o{ COLLECTION : owns
  COLLECTION  ||--o{ REQUEST    : contains
```

---

## State Diagram

State diagrams are useful for documenting lifecycle states — webhooks, job queues,
order statuses, and more.

````markdown
```mermaid
stateDiagram-v2
  [*]      --> Pending
  Pending  --> Running  : job starts
  Running  --> Success  : completes
  Running  --> Failed   : error
  Failed   --> Pending  : retry
  Success  --> [*]
```
````

**Result:**

```mermaid
stateDiagram-v2
  [*]      --> Pending
  Pending  --> Running  : job starts
  Running  --> Success  : completes
  Running  --> Failed   : error
  Failed   --> Pending  : retry
  Success  --> [*]
```

---

## Tips

- Mermaid diagrams adapt automatically to light and dark mode.
- Keep diagrams small and focused — one concept per diagram is easier to read.
- For complex architecture diagrams, consider splitting into multiple focused diagrams
  rather than one large one.
- Full Mermaid syntax reference: [mermaid.js.org](https://mermaid.js.org/intro/)
