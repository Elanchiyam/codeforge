# Submission API Specification

Base path: `/api/v1`

## POST /submissions

Authentication: Required.

Purpose: Create a code submission.

Request:

```json
{
  "problemId": "uuid",
  "language": "JAVA",
  "sourceCode": "public class Solution { ... }"
}
```

MVP response:

`202 Accepted` is recommended if the API models submission as asynchronous, even if execution is temporarily simulated.

Example:

```json
{
  "submissionId": "uuid",
  "status": "QUEUED"
}
```

Future lifecycle:

```text
QUEUED
  |
  v
RUNNING
  |
  +--> ACCEPTED
  +--> WRONG_ANSWER
  +--> COMPILATION_ERROR
  +--> RUNTIME_ERROR
  +--> TIME_LIMIT_EXCEEDED
  +--> MEMORY_LIMIT_EXCEEDED
  +--> SYSTEM_ERROR
```

## GET /submissions/{submissionId}

Authentication: Required.

Users may retrieve their own submission.

Authorization rules:

- A normal user can retrieve only their own private submission.
- Admin access is controlled separately.
- Source code exposure should be considered carefully for future public-submission features.

## GET /users/me/submissions

Authentication: Required.

Supports:

- Pagination
- Status filter
- Problem filter
- Language filter
- Date range in future versions

Example:

```text
GET /api/v1/users/me/submissions?page=0&size=20&status=ACCEPTED
```

## Idempotency

The future submission API should support an `Idempotency-Key` header to prevent accidental duplicate logical submissions caused by client retries.

Example:

```text
Idempotency-Key: 3f1d...
```

The exact storage and expiration strategy will be documented before implementation.

## Internal/Future Execution Contract

The public API must not expose hidden test cases or execution infrastructure.

A future internal message/event might contain:

```json
{
  "submissionId": "uuid",
  "problemId": "uuid",
  "language": "JAVA",
  "sourceCodeReference": "secure-reference"
}
```

Source code should not be unnecessarily copied across multiple systems.
