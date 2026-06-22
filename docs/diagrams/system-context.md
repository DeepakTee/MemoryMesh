# System Context Diagrams

## Component View

```mermaid
flowchart TB
    subgraph Clients
        Agent[AI Agent]
        App[Application Backend]
        Admin[Admin Tool]
    end

    subgraph MemoryMesh
        API[Memory API]
        Retrieval[Retrieval Service]
        Worker[Memory Worker]
        Authz[Authorization Adapter]
    end

    subgraph Infrastructure
        Kafka[(Kafka)]
        Postgres[(PostgreSQL)]
        Vector[(Vector Index)]
        OpenFGA[(OpenFGA)]
        Observability[(Logs / Metrics / Traces)]
    end

    Agent --> API
    App --> API
    Agent --> Retrieval
    Admin --> Retrieval

    API --> Kafka
    Kafka --> Worker
    Worker --> Postgres
    Worker --> Vector

    Retrieval --> Authz
    Authz --> OpenFGA
    Retrieval --> Postgres
    Retrieval --> Vector

    API --> Observability
    Worker --> Observability
    Retrieval --> Observability
```

## Event Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Candidate
    Candidate --> Validated
    Validated --> Published
    Published --> Persisted
    Persisted --> Projected
    Projected --> Indexed
    Indexed --> Queryable

    Validated --> Rejected
    Published --> Retry
    Retry --> Published
```

## Memory Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Created
    Created --> Active
    Active --> Updated
    Updated --> Active
    Active --> Merged
    Merged --> Active
    Active --> Archived
    Archived --> Active
    Active --> Deleted
    Deleted --> [*]
```

## Two-Week MVP Boundary

```mermaid
flowchart LR
    API[Memory API] --> Kafka[(Kafka)]
    Kafka --> Worker[Worker]
    Worker --> DB[(PostgreSQL)]
    DB --> Retrieval[Retrieval API]
    Retrieval --> Response[Ranked Memory Results]
```

The MVP should stop here. Do not add UI, agent orchestration, SaaS billing, or unnecessary product features before the backend system is demonstrably reliable.