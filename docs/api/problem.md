# Problem API Specification

Base path: `/api/v1`

## GET /problems

Browse published problems.

Supported query parameters:

- `page`
- `size`
- `search`
- `difficulty`
- `tag`
- `sort`
- `direction`

Example:

```text
GET /api/v1/problems?page=0&size=20&difficulty=MEDIUM&tag=ARRAY
```

Response:

```json
{
  "content": [
    {
      "id": "uuid",
      "title": "Two Sum",
      "difficulty": "EASY",
      "tags": ["ARRAY", "HASHING"]
    }
  ],
  "page": 0,
  "size": 20,
  "totalElements": 1,
  "totalPages": 1
}
```

Rules:

- Only published problems are returned.
- Maximum page size must be enforced.
- Hidden test cases are never returned.

## GET /problems/{problemId}

Returns the public details of a problem.

Response may include:

- ID
- Title
- Description
- Difficulty
- Examples
- Constraints
- Tags
- Time limit
- Memory limit
- Supported languages

Hidden test cases must not be included.

## POST /admin/problems

Authentication: ADMIN

Creates a problem.

## PUT /admin/problems/{problemId}

Authentication: ADMIN

Updates a problem.

## DELETE /admin/problems/{problemId}

Authentication: ADMIN

Unpublishes/deactivates a problem. Prefer logical deletion where historical submissions must remain valid.

## Future Endpoints

```text
GET /problems/daily
GET /problems/random
GET /problems/recommended
GET /problems/trending
GET /problems/bookmarks
POST /problems/{problemId}/bookmark
DELETE /problems/{problemId}/bookmark
```

These are intentionally excluded from the MVP implementation until the core domain is stable.
