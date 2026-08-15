# Database Entities - MVP

## User

Fields:

- id
- email
- password_hash
- display_name
- role
- status
- created_at
- updated_at

Constraints:

- email unique
- role not null
- status not null

## Problem

Fields:

- id
- title
- description
- difficulty
- time_limit_ms
- memory_limit_mb
- status
- created_by
- created_at
- updated_at

## Problem Tag

Fields:

- problem_id
- tag

A normalized tag table may be introduced depending on search requirements.

## Test Case

Fields:

- id
- problem_id
- input_data/reference
- expected_output/reference
- visibility
- created_at

Important:

Hidden test cases require stronger protection than normal application data.

## Submission

Fields:

- id
- user_id
- problem_id
- language
- source_code/reference
- status
- execution_time_ms
- memory_used_mb
- result_message
- created_at
- completed_at

## Design Considerations

Problem versioning should be considered before the execution engine is introduced. A submission should remain reproducible even if a problem's description or test cases change later.

Source code may eventually be stored in secure object storage rather than directly in the relational database.
