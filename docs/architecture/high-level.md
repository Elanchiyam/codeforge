# High-Level Architecture

## Architecture Evolution

CodeForge will intentionally evolve through multiple architectures.

### Stage 1: Monolith

```text
Client
   |
   v
Spring Boot Application
   |
   v
PostgreSQL
```

The first implementation is a modular monolith.

Modules:

- Authentication
- User
- Problem
- Submission

This allows business rules and transaction boundaries to be understood before distributed-system complexity is introduced.

### Stage 2: Containerized Application

```text
Client
   |
Spring Boot Container
   |
PostgreSQL Container
```

Podman will be used locally.

### Stage 3: Microservices

```text
                 API Gateway / APIM
                         |
        +----------------+----------------+
        |        |        |       |       |
       Auth   Problem  Submission  User  Future Services
                                  |
                              PostgreSQL
```

Service boundaries will be extracted based on domain ownership, not merely by creating a service for every database table.

### Stage 4: Event-Driven

```text
Submission Service
       |
       | SubmissionCreated
       v
     Kafka
       |
       v
Execution Service

Execution Service
       |
       | ExecutionCompleted
       v
     Kafka
       |
       +--> Submission/Statistics
       +--> Notification
       +--> Leaderboard
```

### Stage 5: Azure

Target platform:

- Azure Container Registry
- Azure Kubernetes Service
- Azure API Management
- Azure Key Vault
- Azure Service Bus
- Azure Blob Storage
- Application Insights/Azure Monitor

## Architecture Principles

1. Each service owns its domain.
2. Services should be independently deployable.
3. Database ownership should follow service boundaries.
4. Synchronous calls should be used where immediate response is required.
5. Asynchronous messaging should be used for long-running or decoupled workflows.
6. No distributed database transaction should be required for normal business flows.
7. Observability is part of the system, not an afterthought.
8. Security boundaries must be explicit.
9. Code execution must be isolated from application services.

## Key Future Decision

Kafka and Azure Service Bus may coexist, but they will have different responsibilities.

Kafka is intended for high-throughput event streaming, replayable events, and multiple consumers.

Azure Service Bus is intended for enterprise messaging patterns such as commands, queues, retries, dead-lettering, and scheduled delivery where appropriate.

The exact division will be documented in an ADR when messaging is introduced.
