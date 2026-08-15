# Non-Functional Requirements

## 1. Performance

### NFR-PERF-001

Standard read APIs should target a p95 response time below 500 ms under the defined MVP load, excluding intentionally asynchronous operations.

### NFR-PERF-002

Submission creation should return quickly after durable acceptance of the submission request. Long-running execution must not block the HTTP request in the future architecture.

### NFR-PERF-003

Pagination must prevent unbounded result sets.

## 2. Scalability

### NFR-SCALE-001

Stateless application services should support horizontal scaling.

### NFR-SCALE-002

Services must avoid relying on local in-memory state for business-critical information.

### NFR-SCALE-003

Long-running execution must be independently scalable from API services.

## 3. Availability

The target for the deployed MVP is 99.9% service availability where supported by the selected Azure architecture and subscription tier.

## 4. Reliability

The platform shall:

- Handle transient downstream failures.
- Use bounded retries.
- Avoid retry storms.
- Support idempotent operations where duplicate requests/events are possible.
- Preserve failed asynchronous messages using retry/dead-letter strategies.
- Record sufficient diagnostics for incident investigation.

## 5. Consistency

Strong consistency shall be used inside appropriate transactional boundaries.

Cross-service workflows shall not depend on a distributed database transaction. Future distributed workflows will use asynchronous events and/or Saga-style compensation.

## 6. Security

The platform shall:

- Hash passwords using a strong adaptive password hashing algorithm such as BCrypt.
- Use HTTPS in deployed environments.
- Authenticate protected endpoints.
- Authorize operations using roles/permissions.
- Validate all input.
- Prevent SQL injection through parameterized persistence mechanisms.
- Never expose hidden test cases publicly.
- Never log passwords, access tokens, refresh tokens, or source-code secrets.
- Store production secrets outside source control.
- Apply rate limiting to sensitive APIs in later phases.
- Isolate code execution from the application API layer.

## 7. Observability

The platform shall support:

- Structured logs.
- Correlation/trace IDs.
- Health checks.
- Application metrics.
- Distributed traces in the microservice phase.
- Dashboards and alerting in the cloud phase.

## 8. Maintainability

The codebase shall follow:

- SOLID principles.
- Clear package/module boundaries.
- Consistent naming.
- Small, focused services.
- Automated tests.
- API documentation.
- Architecture Decision Records (ADRs).

## 9. Deployment

The platform shall be containerized using Podman-compatible OCI images.

The target cloud platform is Microsoft Azure, with AKS as the Kubernetes runtime.

## 10. Disaster Recovery

A future production configuration should define:

- Database backups.
- Recovery Point Objective (RPO).
- Recovery Time Objective (RTO).
- Infrastructure recreation strategy.
- Recovery testing.

Exact RPO/RTO values will be decided before production readiness.

## 11. Data Retention

Retention rules shall be defined for:

- User data.
- Submissions.
- Execution logs.
- Audit events.
- Application logs.

The MVP may use simplified retention rules.
