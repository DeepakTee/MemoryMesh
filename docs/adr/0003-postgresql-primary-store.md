# ADR 0003: PostgreSQL as Primary Store

## Status

Accepted

## Context

MemoryMesh needs durable storage for events, projections, tenant data, source metadata, and searchable facts.

## Decision

Use PostgreSQL as the primary database for the first two months.

## Why

PostgreSQL gives us:

- relational modeling
- JSONB
- indexes
- transactions
- full-text search
- optional vector support
- simple local development

## Tradeoffs

- write scaling may need partitioning later
- indexing must be designed carefully
- specialized stores may outperform it for narrow workloads

## Rule

Do not add another primary datastore until benchmark data proves PostgreSQL is the bottleneck.