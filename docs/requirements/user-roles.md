# User Roles and Permissions

## Guest

Can:

- Register.
- Login.
- Browse published problems.
- View published problem details.

Cannot:

- Submit solutions.
- Access private user data.
- Create or modify problems.

## User

Can:

- View/update own profile.
- Change own password.
- Browse problems.
- Search/filter/sort problems.
- Submit solutions.
- View own submission history.
- View own submission details.

Future permissions:

- Bookmark problems.
- Join contests.
- View statistics.
- Participate in discussions.

## Admin

Can:

- Perform all permitted user actions.
- Create problems.
- Update problems.
- Unpublish/delete problems.
- Manage test cases.
- Review platform submissions.
- Manage contests in future versions.

## Security Principle

Authorization must be enforced server-side. The client must never be trusted to enforce permissions.
