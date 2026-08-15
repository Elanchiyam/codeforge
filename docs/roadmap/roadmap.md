# CodeForge Roadmap

## Phase 1 - Modular Monolith

Learn/build:

- Java 21
- Spring Boot
- PostgreSQL
- Flyway
- Spring Security
- JWT
- REST APIs
- Validation
- Exception handling
- Transactions
- AOP
- Unit/integration testing

Deliverable: Working MVP.

## Phase 2 - Podman

Learn/build:

- Containerfile
- OCI images
- Image layers
- Networks
- Volumes
- Podman Compose
- Environment configuration

Deliverable: Entire application runs locally using containers.

## Phase 3 - Microservices

Extract:

1. Auth/User
2. Problem
3. Submission
4. Notification
5. Execution

Start with synchronous REST where appropriate.

## Phase 4 - Kubernetes/AKS

Learn:

- Pods
- Deployments
- Services
- ConfigMaps
- Secrets
- Ingress
- Probes
- Resource limits
- HPA
- Helm
- Rolling deployments

## Phase 5 - Azure

Introduce:

- ACR
- AKS
- APIM
- Key Vault
- Application Insights
- Azure Monitor
- Blob Storage

## Phase 6 - Kafka

Introduce event-driven submission processing.

Events:

- SubmissionCreated
- ExecutionStarted
- ExecutionCompleted
- SubmissionFinalized

Learn:

- Topics
- Partitions
- Consumer groups
- Offsets
- Ordering
- Retries
- Idempotency
- At-least-once delivery
- Dead-letter/recovery strategies
- Schema evolution

## Phase 7 - Azure Service Bus

Use for selected enterprise messaging use cases where queues/commands, scheduled delivery, sessions, retries, and dead-lettering are valuable.

The project will deliberately compare Kafka and Service Bus rather than using both without a reason.

## Phase 8 - Redis

Use for:

- Problem caching
- User/session-related caching where appropriate
- Leaderboard data
- Rate limiting where appropriate

## Phase 9 - Observability

Introduce:

- Micrometer
- Prometheus
- Grafana
- OpenTelemetry
- Application Insights
- Distributed tracing
- Alerts

## Phase 10 - Secure Execution Engine

Build a controlled Java execution pipeline.

Later languages:

- Python
- C++
- JavaScript

## Phase 11 - Advanced Product Features

- Contests
- Leaderboards
- Statistics
- Bookmarks
- Discussions
- Notifications
- Daily challenge
- Recommendations
- AI hints
- Code similarity

## Phase 12 - Production Hardening

- Load testing
- Chaos/failure testing
- Security review
- Backup/recovery
- Cost optimization
- Capacity planning
- SLOs/SLIs
- Runbooks
