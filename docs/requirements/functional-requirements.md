# Functional Requirements

## 1. Scope

The MVP provides authentication, user profiles, problem management, and submission management. Code execution is initially simulated so that the domain and APIs can be validated before introducing execution infrastructure.

## 2. Authentication

### FR-AUTH-001 Registration

A guest shall be able to register using a unique email address and password.

Validation:

- Email must be syntactically valid.
- Email must be unique.
- Password must satisfy configured complexity rules.
- Required fields must not be null or blank.

The password must never be stored in plain text.

### FR-AUTH-002 Login

A registered user shall be able to authenticate using email and password.

Successful authentication returns:

- Access token.
- Refresh token.
- User identity/role information where appropriate.

### FR-AUTH-003 Refresh Token

A user shall be able to obtain a new access token using a valid refresh token.

### FR-AUTH-004 Logout

A user shall be able to invalidate their refresh-token/session state according to the selected token strategy.

### FR-AUTH-005 Role-Based Authorization

The platform shall support at least:

- USER
- ADMIN

Administrative operations shall require ADMIN authorization.

## 3. User Profile

### FR-USER-001 View Own Profile

Authenticated users shall be able to retrieve their profile.

### FR-USER-002 Update Own Profile

Authenticated users shall be able to update permitted profile fields.

### FR-USER-003 Change Password

Authenticated users shall be able to change their password after satisfying authentication and password validation requirements.

### FR-USER-004 Account Deactivation

The platform shall support user account deactivation. Physical deletion may be deferred depending on retention/audit requirements.

## 4. Problem Management

A problem represents a programming challenge.

A problem may contain:

- Title.
- Description.
- Difficulty.
- Tags.
- Constraints.
- Examples.
- Time limit.
- Memory limit.
- Supported languages.
- Publication status.
- Creation/update metadata.

### FR-PROB-001 Browse Problems

Guests and authenticated users shall be able to browse published problems.

### FR-PROB-002 View Problem

Users shall be able to retrieve the details of a published problem.

Hidden test cases must never be returned by public APIs.

### FR-PROB-003 Search Problems

Users shall be able to search problems by title and/or supported searchable text.

### FR-PROB-004 Filter Problems

Users shall be able to filter by:

- Difficulty.
- Tags.
- Publication status where authorized.

### FR-PROB-005 Sort Problems

Users shall be able to sort supported result fields.

### FR-PROB-006 Pagination

Problem listing APIs shall support pagination and enforce a maximum page size.

### FR-PROB-007 Create Problem

Admins shall be able to create a problem.

### FR-PROB-008 Update Problem

Admins shall be able to update a problem.

### FR-PROB-009 Delete/Unpublish Problem

Admins shall be able to remove a problem from public availability. Prefer soft deletion/unpublishing where historical submissions must remain valid.

### FR-PROB-010 Test Cases

Admins shall be able to define visible and hidden test cases.

Hidden test cases shall be accessible only to trusted backend components.

## 5. Submission Management

A submission represents a user's attempt to solve a problem.

A submission contains:

- Submission ID.
- User ID.
- Problem ID.
- Programming language.
- Source code or source-code reference.
- Status.
- Execution time where available.
- Memory usage where available.
- Created timestamp.
- Result/error information where appropriate.

### FR-SUB-001 Create Submission

An authenticated user shall be able to submit code for a published problem.

### FR-SUB-002 Submission Status

The platform shall expose submission status.

Initial/future statuses include:

- QUEUED
- RUNNING
- ACCEPTED
- WRONG_ANSWER
- COMPILATION_ERROR
- RUNTIME_ERROR
- TIME_LIMIT_EXCEEDED
- MEMORY_LIMIT_EXCEEDED
- SYSTEM_ERROR
- CANCELLED

For the MVP, execution may be simulated.

### FR-SUB-003 Submission Details

An authenticated user shall be able to view their own submission details.

### FR-SUB-004 Submission History

An authenticated user shall be able to view their own submission history with pagination and filtering.

### FR-SUB-005 Authorization

Users must not access another user's private submission details unless a future public-submission feature explicitly permits it.

## 6. Future Statistics

Statistics are intentionally excluded from the MVP's core user API.

Future statistics may include:

- Total solved.
- Easy/medium/hard solved counts.
- Total submissions.
- Acceptance rate.
- Current streak.
- Longest streak.
- Contest rating.
- Ranking.

A future Statistics/Leaderboard capability will own these derived metrics rather than the basic User service.

## 7. Future Bookmarks

Users may later:

- Bookmark a problem.
- Remove a bookmark.
- List bookmarked problems.

## 8. Future Contests

The platform may later support:

- Contest creation.
- Contest registration.
- Start/end time.
- Contest problems.
- Submission restrictions.
- Contest scoring.
- Contest leaderboard.

## 9. Future Notifications

The platform may later notify users about:

- Submission completion.
- Contest reminders.
- Account events.
- Announcements.

## 10. Future Code Execution

The execution platform will eventually:

1. Receive a submission job.
2. Fetch the required problem/test-case metadata.
3. Compile source code.
4. Execute code in an isolated sandbox.
5. Apply CPU/memory/time limits.
6. Compare output.
7. Produce an execution result.
8. Publish the result.
9. Persist the submission outcome.
