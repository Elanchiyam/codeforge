# Database Relationships

## MVP Logical Relationships

```text
User 1 -------- * Submission

Problem 1 ----- * Submission

Problem 1 ----- * TestCase

Problem * ----- * Tag
```

## Ownership

User owns:

- Profile information.
- Authentication identity.
- User submissions.

Problem domain owns:

- Problem metadata.
- Problem publication state.
- Test cases.
- Tags.

Submission domain owns:

- Submission lifecycle.
- Submission status.
- Execution result metadata.

## Microservice Evolution

The initial monolith may use one PostgreSQL database with separate schemas/tables.

After service extraction, database ownership should become:

```text
Auth/User Service -> User data

Problem Service -> Problem/Test Case data

Submission Service -> Submission data

Execution Service -> Execution metadata
```

Cross-service joins should not be used as an architectural dependency.

Derived data such as statistics should be rebuildable from authoritative data/events where practical.
