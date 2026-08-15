# Business Rules

## Authentication

BR-AUTH-001: Email addresses must be unique.

BR-AUTH-002: Passwords must be stored only as secure password hashes.

BR-AUTH-003: Access tokens must have a limited lifetime.

BR-AUTH-004: Refresh tokens must be handled securely and must not be exposed in logs.

## Problems

BR-PROB-001: Only published problems are visible through public problem APIs.

BR-PROB-002: Hidden test cases must never be included in public responses.

BR-PROB-003: An unpublished/deleted problem must not accept new submissions unless explicitly allowed by a future business rule.

BR-PROB-004: A problem must have a valid difficulty.

BR-PROB-005: A problem must have a unique stable identifier.

BR-PROB-006: Historical submissions must remain interpretable even if a problem is later edited. The long-term design should therefore consider problem versioning or immutable submission metadata.

## Submissions

BR-SUB-001: Only authenticated users can submit solutions.

BR-SUB-002: A submission must reference an existing published problem.

BR-SUB-003: A submission belongs to exactly one user.

BR-SUB-004: Users can view their own private submission details.

BR-SUB-005: Duplicate submission requests must not accidentally create multiple logical submissions when an idempotency mechanism is used.

BR-SUB-006: Execution results are immutable from the user's perspective after finalization, except for controlled administrative correction.

## Future Execution

BR-EXEC-001: User code must execute in an isolated environment.

BR-EXEC-002: CPU, memory, execution time, process count, and filesystem access must be restricted.

BR-EXEC-003: The execution environment must not have unrestricted access to internal services or production credentials.

BR-EXEC-004: Execution workers must be independently scalable.

## Future Statistics

Derived statistics must be treated as rebuildable data where practical. The source of truth should remain submissions/events rather than manually edited counters.
