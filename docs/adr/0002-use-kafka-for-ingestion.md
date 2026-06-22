# ADR 0002: Use Kafka for Ingestion

## Status

Accepted

## Context

MemoryMesh needs to accept memory writes without tightly coupling API latency to downstream processing.

## Decision

Use Kafka as the ingestion backbone for memory events.

## Alternatives Considered

- Direct database writes from API
- RabbitMQ
- Redis streams
- Kafka

## Why Kafka

Kafka is appropriate because it provides:

- durable event streams
- consumer groups
- replay capability
- partitioning
- backpressure handling
- strong interview relevance for distributed systems roles

## Consequences

### Positive

- API and worker are decoupled
- consumers can scale independently
- projections can be rebuilt from retained events
- failures are easier to reason about

### Negative

- higher local setup complexity
- requires idempotent consumers
- introduces eventual consistency

## Rule

The API accepts a write only after the event is published successfully. The worker owns projection updates.