# Security Requirements

## Authentication

Use Spring Security with token-based authentication.

Passwords must be hashed using BCrypt or an equivalent adaptive password hashing algorithm.

## Authorization

Use role-based authorization for MVP.

Roles:

- USER
- ADMIN

Authorization must be enforced at the API/service boundary.

## JWT

Access tokens:

- Short lived.
- Signed with a secure key.
- Must contain only necessary claims.

Refresh tokens:

- Must be protected.
- Must not be logged.
- Must have controlled lifetime/revocation strategy.

## Secrets

Local development secrets may use environment variables or local secret configuration.

Cloud secrets must not be committed to Git.

Target:

Azure Key Vault + managed identity.

## API Security

Apply:

- Input validation.
- Authentication.
- Authorization.
- HTTPS.
- Rate limiting for authentication/submission endpoints.
- Safe error responses.
- Request size limits.

## Code Execution Security

The execution service is a high-risk component.

User-submitted code must not execute inside the main API container.

The eventual execution architecture must provide:

- Process isolation.
- CPU limits.
- Memory limits.
- Timeouts.
- Restricted filesystem.
- Restricted network access.
- No access to Azure credentials.
- No access to production databases.
- Temporary workspace cleanup.
- Worker-level resource limits.

This area requires a dedicated security review before production use.
