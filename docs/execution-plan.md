# MemoryMesh Execution Plan

## Rule Before You Start

Do not code randomly. Every implementation task must map to one of the GitHub issues.

This project is not judged by how many features exist. It is judged by how clearly the system demonstrates infrastructure thinking.

## Week 1: Architecture and Foundation

### Goal

Create the technical foundation and local development environment.

### Work

- Complete RFC 0001.
- Create monorepo layout.
- Add Docker Compose.
- Run PostgreSQL locally.
- Run Kafka locally.
- Add OpenFGA locally.
- Add Makefile commands.

### Output

A reviewer should understand the system before reading code.

## Week 2: MVP

### Goal

Complete the first end-to-end memory flow.

### Work

- Create memory event API.
- Publish events to Kafka.
- Consume events in worker.
- Persist events to PostgreSQL.
- Maintain current memory projection.
- Add basic retrieval endpoint.
- Add semantic, keyword, and recency scoring.

### Output

Demo: submit memory, process it, retrieve it.

## Week 3: Authorization

### Goal

Make the system look enterprise-grade.

### Work

- Define OpenFGA model.
- Add tenant, user, team, memory relationships.
- Enforce access checks in retrieval.
- Add authorization tests.

### Output

Demo: unauthorized user cannot retrieve restricted memory.

## Weeks 4-5: Benchmarking

### Goal

Prove scale characteristics.

### Work

- Generate synthetic memory dataset.
- Test 100K, 1M, and stretch 10M memory records.
- Measure ingestion throughput.
- Measure retrieval latency.
- Document bottlenecks.

### Output

A benchmark report with actual numbers.

## Week 6: Reliability

### Goal

Show operational maturity.

### Work

- Restart consumers during processing.
- Pause and resume Kafka.
- Restart PostgreSQL.
- Verify duplicate handling.
- Document recovery behavior.

### Output

A failure and recovery report.

## Week 7: Observability

### Goal

Make the system operable.

### Work

- Structured logs.
- Metrics.
- Traces.
- Dashboard.
- Projection lag metric.
- Retrieval latency metric.

### Output

A local dashboard showing system health.

## Week 8: Case Study

### Goal

Convert the project into interview leverage.

### Work

- Final architecture writeup.
- Benchmark report.
- Tradeoff analysis.
- Interview talking points.
- Resume bullet.

### Output

A Staff-level project narrative.

## Anti-Goals

Do not build these before the core platform works:

- frontend UI
- chatbot wrapper
- SaaS billing
- authentication product
- agent framework
- LangGraph integration
- unnecessary Kubernetes setup

## Daily Execution Loop

1. Pick one issue.
2. Write expected behavior.
3. Implement minimum working version.
4. Add tests or reproducible demo.
5. Update docs.
6. Commit.
7. Move to next issue.

If you cannot explain why a task improves the system, do not do it.