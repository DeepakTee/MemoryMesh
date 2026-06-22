# ADR 0001: Use Go for Core Services

## Status

Accepted

## Context

MemoryMesh is intended to demonstrate infrastructure engineering, not just AI application development. Core services need to handle network APIs, Kafka consumers, concurrency, and operational workloads.

## Decision

Use Go for core MemoryMesh services.

## Why

Go is a strong fit for infrastructure systems because it provides:

- simple concurrency primitives
- fast compile times
- straightforward deployment
- strong standard library
- common usage in infrastructure companies
- good support for HTTP, gRPC, Kafka clients, and observability

## Consequences

Positive:

- improves employability for platform and infra roles
- keeps runtime simpler than JVM-based services
- forces clean service boundaries

Negative:

- slower initial development if the builder is more experienced in Python
- fewer high-level AI libraries than Python

## Implementation Note

Python may still be used for benchmark scripts, synthetic data generation, or offline evaluation, but core runtime services should remain in Go.