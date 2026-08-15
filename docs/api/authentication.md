# Authentication API Specification

Base path: `/api/v1`

## POST /auth/register

Purpose: Register a new user.

Request:

```json
{
  "email": "user@example.com",
  "password": "StrongPassword123",
  "displayName": "User"
}
```

Success: `201 Created`

Example:

```json
{
  "userId": "uuid",
  "email": "user@example.com",
  "displayName": "User"
}
```

Errors:

- `400` validation failure
- `409` email already exists

## POST /auth/login

Purpose: Authenticate a user.

Request:

```json
{
  "email": "user@example.com",
  "password": "StrongPassword123"
}
```

Success: `200 OK`

Example:

```json
{
  "accessToken": "<token>",
  "refreshToken": "<token>",
  "tokenType": "Bearer",
  "expiresIn": 900
}
```

Errors:

- `401` invalid credentials
- `429` rate limited in future production configuration

## POST /auth/refresh

Purpose: Obtain a new access token.

Request:

```json
{
  "refreshToken": "<token>"
}
```

Success: `200 OK`

## POST /auth/logout

Purpose: Invalidate refresh-token/session state.

Authentication: Required.

Success: `204 No Content`

## Security

- Passwords are never returned.
- Tokens must not be logged.
- Access tokens are short lived.
- Refresh token handling will be hardened before production deployment.
