# MemoryMesh Interview Guide

Use this file to prepare the final story once the project is implemented.

## One-Line Pitch

MemoryMesh is a distributed memory infrastructure platform for AI applications, built with streamed ingestion, PostgreSQL projections, hybrid retrieval, access control, observability, and reliability testing.

## 60-Second Explanation

Most AI apps treat memory as embeddings in a vector database. I wanted to explore the harder infrastructure problem: how memory should be stored, updated, retrieved, authorized, observed, and recovered in a production-like system.

MemoryMesh accepts memory events, streams them through Kafka, stores durable history in PostgreSQL, builds queryable projections, supports hybrid retrieval, and checks access before returning results.

## Deep-Dive Topics

### 1. Why event-style memory?

Explain:

- current state is not enough
- history matters
- source tracking matters
- projections can be rebuilt

### 2. Why Kafka?

Explain:

- decoupling API from workers
- replay
- consumer groups
- async processing

### 3. Why PostgreSQL?

Explain:

- simpler first datastore
- transactions
- indexing
- JSONB
- full-text search
- benchmark before adding complexity

### 4. Retrieval Design

Explain:

- semantic search for meaning
- keyword search for exact facts
- recency for freshness
- confidence for reliability
- access checks before returning results

### 5. Reliability

Explain:

- duplicate events
- worker restart
- projection rebuild
- invalid event isolation
- measurable projection lag

### 6. Observability

Explain:

- structured logs
- ingestion latency
- retrieval latency
- consumer lag
- projection lag
- error rates

## Questions Interviewers May Ask

### Why not just use a vector database?

Because memory is not only retrieval. Production memory needs lifecycle, provenance, access control, current-state projection, and operational visibility.

### Why not write directly to PostgreSQL?

Direct writes are simpler but tightly couple API latency to downstream processing. Kafka gives decoupling, replay, and worker scalability.

### What consistency model does the system use?

Eventual consistency between write acceptance and retrieval projection. The system should expose projection lag so clients understand freshness.

### What would you improve with more time?

- partitioned event tables
- stronger evaluation framework
- memory conflict handling
- multi-region deployment
- richer access model
- production-grade tracing

## Final Resume Bullet Draft

Built MemoryMesh, a distributed memory infrastructure platform for AI applications using Go, Kafka, PostgreSQL, and OpenFGA, implementing streamed ingestion, hybrid retrieval, access control, observability, and reliability testing for production-like AI memory workflows.