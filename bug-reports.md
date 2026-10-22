# Sample Defect Reports — TeamSpace

**Important:** These are fictional examples written to demonstrate defect-reporting technique. They have not been observed or verified in a real application. Treat the “Actual Result” as a hypothetical result for the example only.

## BUG-001 — Removed team member can still access team chat

**Type:** Functional / Authorization  
**Suggested severity:** High  
**Suggested priority:** High  
**Environment:** Fictional test environment; record actual build and device during execution  
**Status:** Example only — not verified

### Description

A user who has been removed from a team may still be able to open the former team's chat and read restricted messages.

### Preconditions

- A team and team chat exist.
- A synthetic test account is a member of that team.
- An admin account can remove members.

### Steps to reproduce

1. Sign in as the admin.
2. Open the team roster.
3. Remove the synthetic test account from the team.
4. Sign in as the removed account.
5. Open Chat or Archived Chats.
6. Attempt to open the former team's conversation.

### Expected result

The removed account cannot access restricted team chat content after removal, in accordance with the product's access-control requirements.

### Hypothetical actual result

The former team conversation remains accessible and displays messages.

### Evidence to collect during real execution

- Screenshot or recording of the removal action.
- Screenshot showing the account's role/membership state.
- Screenshot or recording of the attempted chat access.
- Build, OS/browser, account role, and execution timestamp (using synthetic accounts).

### Notes

Confirm whether historical chat access is intentionally retained before filing this as a confirmed defect. If the intended behavior is unclear, raise a requirement question first.

---

## BUG-002 — Staff without announcement permission can publish an announcement

**Type:** Authorization / Functional  
**Suggested severity:** High  
**Suggested priority:** High  
**Environment:** Fictional test environment  
**Status:** Example only — not verified

### Description

A staff account without announcement-publishing permission may be able to publish an announcement.

### Preconditions

- A team exists.
- A staff account is assigned to the team.
- The staff account's announcement permission is disabled.

### Steps to reproduce

1. Sign in as an admin.
2. Confirm announcement-publishing permission is disabled for the test staff account.
3. Sign in as the staff account.
4. Navigate to Announcements.
5. Attempt to publish a new announcement.
6. If API access is available, attempt the equivalent protected API operation.

### Expected result

The staff account cannot publish an announcement through the UI or directly through the API.

### Hypothetical actual result

The announcement is published despite the permission being disabled.

### Evidence to collect during real execution

- Permission configuration screenshot.
- Account role and team assignment.
- UI result and sanitized API request/response, if applicable.
- Build and environment details.

### Notes

Server-side authorization must be checked independently of whether the UI hides or disables the action.

---

## BUG-003 — Invalid team creation request is accepted

**Type:** API / Data validation  
**Suggested severity:** Medium  
**Suggested priority:** Medium  
**Environment:** Fictional API  
**Status:** Example only — not verified

### Description

The API may accept a create-team request without a required team name.

### Preconditions

- API documentation identifies team name as a required field.
- A test environment and authorized test token are available.

### Steps to reproduce

1. Send the documented create-team request.
2. Omit the required team name.
3. Inspect the HTTP status and response body.
4. Query the test environment to check whether an invalid team was created.

### Expected result

The API rejects the request with the documented validation status and a useful error response. No team record is created.

### Hypothetical actual result

The API returns a success response or creates a team record without a valid name.

### Evidence to collect during real execution

- Sanitized request method, path, and body.
- Response status and response body.
- Follow-up query confirming whether a record was created.
- Environment and build details.

### Notes

Never publish tokens, cookies, private URLs, or sensitive response data in the portfolio.
