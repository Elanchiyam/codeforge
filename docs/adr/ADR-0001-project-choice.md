# ADR-0001: Choose CodeForge as the Learning Project

## Status

Accepted

## Context

The project needs to provide hands-on experience in modern backend engineering rather than only CRUD development.

Required learning areas include:

- Java/Spring Boot
- Transactions
- AOP
- Concurrency
- Containerization
- Kubernetes/AKS
- Azure services
- API Management
- Messaging
- CI/CD
- Observability

## Decision

Build CodeForge, a LeetCode-like coding platform.

## Rationale

A coding platform naturally creates technically meaningful problems:

- Long-running jobs.
- Asynchronous processing.
- Queues.
- Concurrency.
- Resource isolation.
- Idempotency.
- Event-driven architecture.
- Caching.
- Distributed tracing.
- Scaling.

This provides stronger learning opportunities than a simple CRUD application.

## Consequences

Positive:

- Broad backend learning surface.
- Natural microservice boundaries.
- Real reason to introduce Kafka.
- Real reason to introduce Kubernetes.
- Real concurrency challenges.
- Strong portfolio/interview value.

Negative:

- Code execution introduces significant security complexity.
- The project can become too large if scope is not controlled.
- A frontend is not trivial but is intentionally not part of the backend MVP.

## Scope Control

The project starts with a modular monolith and simulated submission execution. Distributed execution and advanced features are introduced only after the core domain is stable.
