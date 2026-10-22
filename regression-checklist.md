# Regression Checklist — TeamSpace

Use this checklist after a change is deployed to a test environment. Mark each item only after execution.

**Execution details**

- Build/version:
- Environment:
- Tester:
- Date:
- Related change/ticket:
- Device/browser:
- Test accounts (synthetic identifiers only):

## Authentication

- [ ] Valid user can sign in.
- [ ] Invalid credentials are rejected.
- [ ] Required-field validation works.
- [ ] Sign-out invalidates access to protected content.
- [ ] Session expiry behavior follows requirements.

## Team and roster

- [ ] Admin can create a team with valid data.
- [ ] Required team fields are validated.
- [ ] Team appears in the correct list after creation.
- [ ] Authorized admin can add a roster member.
- [ ] Invalid member data is rejected.
- [ ] Search and empty states work.
- [ ] Removed members no longer have unauthorized access.
- [ ] Duplicate submissions do not create duplicate records.

## Schedule and events

- [ ] Authorized users can view team events.
- [ ] Event title, date, time, and location are consistent.
- [ ] Time-zone behavior follows documented requirements.
- [ ] Users cannot access restricted team events.

## Announcements and permissions

- [ ] Staff with permission can publish announcements.
- [ ] Staff without permission cannot publish announcements.
- [ ] Empty required content is rejected.
- [ ] Changing a permission updates effective access.
- [ ] Direct URL and API attempts are also permission-checked where applicable.

## Linked accounts

- [ ] Valid guardian invitation links the intended accounts.
- [ ] Invalid or expired invitation is rejected.
- [ ] Guardian can access only permitted linked-athlete information.
- [ ] Unlinking behavior matches documented requirements.

## API

- [ ] Successful requests return documented status codes and response structure.
- [ ] Missing required fields return validation errors.
- [ ] Invalid/nonexistent identifiers are handled consistently.
- [ ] Unauthenticated protected requests are rejected.
- [ ] Unauthorized role actions are rejected server-side.
- [ ] Error responses do not expose secrets or unrelated data.
- [ ] Create/update operations persist only valid data.

## Close-out

- [ ] Failed cases have linked defect reports.
- [ ] Fixes have been retested.
- [ ] Related regression tests have been completed.
- [ ] Remaining failures and risks are documented.
- [ ] Evidence has been checked for confidential information.

## Result summary

| Result | Count |
|---|---:|
| Passed | TBD |
| Failed | TBD |
| Blocked | TBD |
| Not run | TBD |
| Open defects | TBD |

Do not publish guessed execution counts. Replace `TBD` with actual results after testing.
